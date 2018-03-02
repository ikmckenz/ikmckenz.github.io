---
layout: post
title: Electricity demand is very cyclical - a visualization
date: 2018-02-10 14:00:00 -0700
---

Electricity demand is interesting because it demonstrates cyclicality on both daily and yearly timescales. 
The code for this post is available in [this repository][repo]. 

First I grabbed historical data from the [AESO][aeso]. It is in two files, year-to-date and historical.

The first thing we will do is load up the data.

{% highlight python %}
import numpy as np
import pandas as pd
from multiprocessing import cpu_count, Pool
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
from matplotlib import cm
import datetime as dt
import scipy.io

new_demand = pd.read_csv('data/HourlyDemands.csv')
demand = pd.read_csv('data/HourlyDemands_2002-2017.csv')
demand = demand.append(new_demand, ignore_index=True)

# Since the isn't super small, we will multiprocess some things
num_partitions = 16
num_cores = 8

def parallelize_dataframe(df, func):
    df_split = np.array_split(df, num_partitions)
    pool = Pool(num_cores)
    df = pd.concat(pool.map(func, df_split))
    pool.close()
    pool.join()
    return df


def to_datetime(x: pd.DataFrame) -> pd.DataFrame:
    x['Date'] = pd.to_datetime(x['Date'], format='%d-%b-%y')
    return x
{% endhighlight %}

Now that we have all our data loaded up and ready to use, let's look for any long term trend.

{% highlight python %}
df = demand.copy(deep=True)
df.drop(['Total Market Demand', 'Hour'], axis=1, inplace=True)
df = parallelize_dataframe(df, to_datetime)
df.set_index('Date', drop=True, inplace=True)
df = df.resample('Q').mean()
plt.plot(df)
plt.title('Quarterly Electricity Demand')
plt.show()
{% endhighlight %}

What we get from that is this nice plot of the electricity demand by quarter since 2002.

![quarterly_demand]({{ "/assets/electricity_cyclicality/quarterly_demand.png" | absolute_url }})

It's pretty interesting to see that demand is actually decreasing over time. 
I'm not quite sure why this is, as you'd expect it to be increasing. 
Perhaps this is reduced industrial demand or growing efficiency.  

Up next we will get to the star of the show, which is the cyclicality of the demand. 

I want to use the wonderful Matlab/Octave waterfall plot, so I will do some further data chopping with Pandas and then save it as a .mat file.

{% highlight python %}
df = demand.copy(deep=True)
df = parallelize_dataframe(df, to_datetime)
df = df.pivot(index='Date', columns='Hour', values='Ontario Demand')

dates = df.index.strftime("%Y-%m-%d")

scipy.io.savemat('data/z_values.mat', {'mdict': df.values})
scipy.io.savemat('data/x_values.mat', {'mdict': dates})
{% endhighlight %}

And now we generate our wonderful waterfall plot. 

![waterfall]({{ "/assets/electricity_cyclicality/waterfall.png" | absolute_url }})

Pretty cool!
Each day represents once slice, and how the slices move through time is super interesting.
So we can clearly see that demand is lower in the early hours of the morning (~4am seems to be the low point), and is higher in the day.
We can also see that demand is overall higher in the summer and winter, and lower in the spring and fall. 
We still can't see these relationships perfectly, so I made this quick video to really hammer the point home. 
Once again, the code for the plot and everything else is available in this [Github repo][repo].

<div style="width: 100%; height: 0px; position: relative; padding-bottom: 74.971%;"><iframe src="https://streamable.com/s/ob3e2/uioyn" frameborder="0" width="100%" height="100%" allowfullscreen style="width: 100%; height: 100%; position: absolute;"></iframe></div>

Now that is pretty neat. 
One thing that you might notice is that the shape of the daily slice seems to be different in the summer than in the winter.
Let's take a closer look at that by plotting the average summer and winter day.
Jumping back to Python:

{% highlight python %}
df = demand.copy(deep=True)
df = parallelize_dataframe(df, to_datetime)
df = df.pivot(index='Date', columns='Hour', values='Ontario Demand')
# The warmest months in Toronto are June, July, and August, so we use [6,7,8]
summer = df[df.index.month.isin([6, 7, 8])].mean()
# The coldest months are January, Febuary, and December, so we use [1, 2, 12]
winter = df[df.index.month.isin([1, 2, 12])].mean()

plt.plot(summer, 'r', label='Summer')
plt.plot(winter, 'b', label='Winter')
plt.title('Average demand through the day')
plt.xlabel('Hour')
plt.ylabel('Demand')
plt.legend()
plt.show()
{% endhighlight %}

![seasons]({{ "/assets/electricity_cyclicality/demand_seasons.png" | absolute_url }})

As we can see, average summer demand peaks around 3 or 4pm, probably due to air conditioning, while winter demand has an interesting trough mid-day probably due to reduced need for heating while the sun is strongest.

So overall, electricity demand is very cyclical and super interesting.


[repo]: https://github.com/ikmckenz/electricity_cyclicality
[aeso]: http://www.ieso.ca/power-data