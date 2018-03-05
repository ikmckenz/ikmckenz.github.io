---
layout: post
title: Yet another XIV explanation
date: 2018-03-04 14:00:00 -0700
---

Exchange-traded notes like XIV and SVXY have 
[been](https://www.cnbc.com/2018/02/05/xiv-exchange-traded-security-linked-to-volatility-plummets-80-percent.html)
[in](https://www.vox.com/business-and-finance/2018/2/27/17014082/market-crash-inverse-volatility-vix-xiv-svxy)
[the](http://www.businessinsider.com/xiv-svxy-short-vix-volatility-trade-blow-up-2018-2)
[news](https://www.cnbc.com/2018/02/07/credit-suisse-defends-controversial-xiv-etn-amid-market-turmoil.html)
[lately](https://www.forbes.com/sites/jimcollins/2018/02/06/it-works-until-it-doesnt-work-the-death-of-xiv-shows-the-folly-of-gaming-market-volatility/). 
TL;DR: they "blew up" or lost a large amount of their value in a short period of time.
Some of the articles try to describe the products at a high level but very few do a good job of it, and more importantly, none of the articles in question really explain *why* the various products exist. 
Various articles have described these products as "controversial", "obscure", or a "folly", but the reality is that they are (or were) good products that existed for good reasons. 
Everyone and their dog has a blog post talking about the volatility blow up, but I've had to explain the reasoning behind these products many times to friends and family; [enough times that I should write a blog post](https://twitter.com/drob/status/928447584712253440).

Many of my friends and family aren't too financially literate, so I'll start at the very basic and work my way up. 

### Stocks and the S&P 500
Most people have a pretty good high-level understanding of what stocks are, so I'll be quick here. 
A stock is essentially piece of a company. 
When you buy a stock you own a small sliver of that company, and you typically get certain rights with that such as voting on the members of the board of directors (who then decide things such as executive pay), and receiving profits in the form of dividends. 

A stock index is a measurement of a group of stocks. 
Unfortunately, the most-quoted stock index in the media is the Dow Jones Industrial Average, which also happens to be just about the [worst stock index out there](https://www.washingtonpost.com/news/wonk/wp/2013/09/10/the-dow-jones-industrial-average-is-ridiculous/?utm_term=.33e328400ec7).
In the actual financial world, the most important American stock index is the S&P 500, which is a market-capitalization (think *company size*) weighted index of 500 very large companies which are representative of the US economy. 
You can think of it as a single number which is a pretty good representation of the overall stock market. 

### Options, Volatility, and the VIX
There are contracts which *derive* their value from some underlying financial asset or index, and these contracts are called *derivatives*.
One simple example of this is a futures contract, where you pay now and receive the asset in the future (or receive the difference between the price at the future time and what you originally paid). 
One very common example of a derivative is the *option*, which gives its owner the *right* (but not the obligation) to buy or sell some asset at a certain price.
Options are very practical and useful for protecting your portfolio or making tailored bets, and they are interesting because their price relies not only on the price of the underlying asset, but also its volatility (the amount of fluctuation in the price), the amount of time until the option expires, and a few other things.

Let's say we have some company whose stock is currently $100. 
Let's say we have a call option whose strike is $90, with one week to maturity. Because this is a call option and the strike price is below the underlying price, this is called an in-the-money option.
This means we have the right to buy the stock for $90 in one week.
If one week from now the stock price was down at $85, we would lose all the money we payed for the option.
If one week from now the stock price was up at $110, we would exercise the option and collect our $20 happily.
Let's say we have a call options whose strike is $105, with one week to maturity. Because this is a call option and the strike price is above the underlying price, this is called an out-of-the-money option. 
If one week from now the stock price is up above $105 plus whatever we paid for the option we are happy, otherwise we've lost.   

As a quick example on how we might use these, let's say that XYZ Pharmaceutical Company's stock is trading at $100, and tomorrow they announce the results of an important clinical trial. 
* Let's say you own the stock, but you're worried about the results. The stock has been doing well, and you want to lock in some money. You could sell the stock you own, but then you've lost the opportunity to profit from the trial. Alternatively, you could buy a put option with a strike of $100 (you buy the right to sell the stock for $100). This costs you some money, but then tomorrow if the stock price crashes because the trial failed, you don't lose any money. Also, if the stock price jumps because of a successful trial, you make that money. In this case the put option acts almost like "insurance" on your position.
* Let's say you don't own the stock but are very confident about the results of the trial and think the price of the stock will go to $120. You could buy a share for $100, and tomorrow you would have profited $20. Alternatively, let's say you bought 20 call options for $5 each with a strike of $110 (you bought the right to buy the stock for $110). Then tomorrow you've profited $200 instead of $20 from your $100 investment. Pretty nice.
* Let's say you don't know whether the trial will be good or bad, but you think that it will have a big impact on the stock price. Options allow you to profit in this scenario! You can buy a call and a put (sometimes called a [long straddle](https://www.investopedia.com/terms/s/straddle.asp)), and if you are right about the price changing drastically, you will profit. 

In this last example, you essentially made a bet on the "volatility" of the stock increasing.
Volatility is the amount of fluctuation in a price, and options allow you to place bets on it increasing or decreasing. 
This is very useful because it allows you to purchase protection from, or make a bet on the *volatility* of a price, not just the direction of the price.

Now we can introduce a new index, called the VIX or Volatility Index.
Rather than being an index that measures the price performance of a group of stocks, this index measures the *expected volatility* of the S&P 500.
It does this by taking a weighted average of the prices of out-of-the-money options on the S&P 500.
One last point is that you can't really buy the VIX. It's just a number. 
What you can do is buy derivatives which derive their value from the VIX, such as futures and options.

### Crushing the VIX and Leveraged ETPs
For a pretty long period of time, almost two years straight, the price of volatility on the S&P 500 was very, **very** low. 
Before 2017 the VIX closed below 10 a grand total of 9 times. In 2017, it closed below 10 a total of 52 times. 
That massive difference was because of what the media termed the "[volatility trap](https://www.cnbc.com/2015/04/21/the-vix-is-getting-crushed-in-a-volatility-trap.html)" or "crush".
Essentially it had become extremely profitable and then extremely popular to bet against volatility.
Just about every hedge fund was doing it, there's a good chance your pension fund was doing it, finance students around campus started doing it, average investors started doing it too.

But how, you might ask, would average investors get involved with this trade? 
After all, futures are complicated products which can require a large amount of capital to trade.
Have no fear, ETP providers are here.
An ETP is an Exchange Traded Product, essentially a derivative, index, or package of derivatives which is purchased by a fund, who is then listed on an exchange like a company and which you can buy shares of.
Companies such as ProShares and VelocityShares offer them on all sorts of interesting products, such as the VelocityShares UGLD product (triple-leveraged gold price, essentially returning whatever gold returned times 3), their VIIX product which buys the closest two month VIX futures, and of course XIV which shorted the closest two month VIX futures.
The thing about most of these funds, especially the leveraged and short funds, is that they will go to $0 eventually.
This is because leverage and shorting cost money, so eventually they will burn all capital through leverage/shorting fees.
In addition to this, when you are leveraged or shorting you can easily lose more than 100% of the initial investment. To prevent this, the manager of XIV said they would shut down the fund if it ever dropped by 80% in one day.
These facts were never hidden, but rather were loudly proclaimed on [the prospectus](http://app.velocitysharesetns.com/files/prospectus/CS_VIX_VelocityShares_ETN_Amended_Final_Pricing_Supplement_AR48_long_form_2.PDF): 
> As explained in “Risk Factors” in this pricing supplement, because of the way in which the Closing 
Indicative Value of the ETNs and the underlying Indices are calculated, the amount payable at maturity or 
upon redemption or acceleration is likely to be less than the amount of your initial investment in the ETNs, 
and you are likely to lose part or all of your initial investment.  In almost any potential scenario the Closing 
Indicative Value (as defined below) of
 your ETNs is likely to be close to zero after 20 years and we do not 
intend or expect any investor to hold
 the ETNs from inception to maturity. 

But most people didn't listen to this, because the volatility crush was making this trade incredibly profitable.
At the start of 2016 the value of XIV was about $20, and by the end of 2017 it hit above $130. 
Any return to "normal" volatility conditions would wipe very large amounts of money from this product, and people were essentially playing chicken with the VIX.

Then, on February 5th, 2018 the VIX spiked.
Central banks reducing their balance sheets, increasing rates, flattening yield curves, yadda yadda.
The reasons aren't really important, what is important is that this was going to happen eventually.
There was also some talk of the large size of the XIV and SVXY funds meaning they had to buy a lot of VIX futures, which further increased the price, but I don't think this had a very significant impact.
The people who were playing chicken with the VIX lost, big time, but the important point is that this was expected to happen eventually.