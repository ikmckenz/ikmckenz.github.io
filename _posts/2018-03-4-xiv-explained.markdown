---
layout: post
title: Yet another XIV explanation
date: 2018-03-04 14:00:00 -0700
---
Exhcange-traded notes like XIV and SVXY have 
[been](https://www.cnbc.com/2018/02/05/xiv-exchange-traded-security-linked-to-volatility-plummets-80-percent.html)
[in](https://www.vox.com/business-and-finance/2018/2/27/17014082/market-crash-inverse-volatility-vix-xiv-svxy)
[the](http://www.businessinsider.com/xiv-svxy-short-vix-volatility-trade-blow-up-2018-2)
[news](https://www.cnbc.com/2018/02/07/credit-suisse-defends-controversial-xiv-etn-amid-market-turmoil.html)
[lately](https://www.forbes.com/sites/jimcollins/2018/02/06/it-works-until-it-doesnt-work-the-death-of-xiv-shows-the-folly-of-gaming-market-volatility/). 
TL;DR, they "blew up" or lost a large amount of their value in a short period of time.
Some of the articles try to describe the products at a high level but very few do a good job of it, and more importantly, none of the articles in question really explain *why* the various products exist. 
Various articles have described these products as "controversial", "obscure", or a "folly", but the reality is that they are (or were) good products that existed for good reasons. 
I've had to explain the reasoning behind these products many times to friends and family; [enough times that I should write a blog post](https://twitter.com/drob/status/928447584712253440).

Many of my friends and family aren't too financially literate, so I'll start at the very basic and work my way up. 

### Stocks and the S&P 500
Most people have a pretty good high-level understanding of what stocks are, so I'll be quick here. 
A stock is essentially piece of a company. 
When you buy a stock you own a small sliver of that company, and you typically get certain rights with that such as voting on the members of the board of directors (who then decide things such as executive pay), and receiving profits in the form of dividends. 

A stock index is a measurment of a group of stocks. 
Unfortunately, the most-quoted stock index in the media is the Dow Jones Industrial Average, which also happens to be just about the [worst stock index out there](https://www.washingtonpost.com/news/wonk/wp/2013/09/10/the-dow-jones-industrial-average-is-ridiculous/?utm_term=.33e328400ec7).
In the actual financial world, the most important American stock index is the S&P 500, which is a market-capitalization (think *company size*) weighted index of 500 very large companies which are representative of US economy. 
You can think of it as a single number which is a pretty good representation of the overall stock market. 

### Options, Volatility, and the VIX
There are contracts which *derive* their value from some underlying financial asset or index, and these contracts are called *derivatives*. 
One very common example of a derivative is the *option*, which gives its ower the *right* (but not the obligation) to buy or sell some asset at a certain price.
Options are very practical and useful for protecting your portfolio or making tailored bets.
For example, let's say that company XYZ Pharmaceutical Company's stock is trading at $100, and tomorrow they announce the results of an important clinical trial. 
* Let's say you own the stock, but you're worried about the results. The stock has been doing well, and you want to lock in some money. You could sell the stock you own, but then you've lost the opportunity to profit on the trial. Alternatively, you could but a put with a strike of $100 (you buy the right to sell the stock for $100). This costs you some money, but then tomororow if the stock price crashes because the trial failed, you don't lose any money. Also, if the stock price jumps because of a successful trial, you make that money. In this case the put option acts almost like "insurance" on your position.
* Let's say you don't own the stock but are very confident about the results of the trial and think the price of the stock will go to $120. You could buy a share for $100, and tommorow you would have profited $20. Alternatively, let's say you bought 20 call options for $5 each with a strike of $110 (you bought the right to buy the stock for $110). Then tomorrow you've profited $200 from your $200 investment. Pretty nice.
* Let's say you don't know whether the trial will go good or bad, but you think that it will have a big impact on the stock price. Options allow you to profit in this scenario! You can buy a call and a put (sometimes called a [long straddle](https://www.investopedia.com/terms/s/straddle.asp)), and if you are right about the price changing drastically, you will profit. 

In this las example, you essentially made a bet on the "volatility" of the stock increasing.
