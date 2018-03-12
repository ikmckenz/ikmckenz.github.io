---
layout: page
title: Quant Bot
permalink: /quant_bot/
---

A Reddit bot for quantitative finance. 
This bot is just in the beta stage and it's mostly a toy project to learn SQL, but hopefully someone will find it useful.
You can query it using `!quant_bot` on the following subreddits:
Finance, Stocks, Investing, WallStreetBets.
See the code [here](https://github.com/ikmckenz/quant_bot).

## Usage

#### Volatility
See the volatility of a stock over the last year.
Use `!quant_bot vol TICKER`
where TICKER is the stock you are interested in.

#### Histogram
Get a histogram of 5 years of weekly returns with some statistical data.
Use `!quant_bot hist TICKER`
where TICKER is the stock you are interested in.

#### Peer Analysis
Get a detailed peer analysis, inluding a graph of normalized returns for all peers, a table of peers with analytical data, and a correlation matrix generated with one year of price data.
Use `!quant_bot peers TICKER`
where TICKER is the stock you are interested in.

#### More
I've already implemented a couple more things in the code but haven't yet 'activated' them. 
Stay tuned for updates on this page.
