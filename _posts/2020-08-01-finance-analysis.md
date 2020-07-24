---
layout: post
title: Moronic Monday at the Finance sub
tags: [reddit]
comments: true
published: true
---

Every Monday at the [Finance sub](https://old.reddit.com/r/finance/), a new thread will be posted to allow the community to ask questions anything about finance such as financial careers, homework problems and finance in general. Some of the questions asked may be quite simple and could be easily googled and others are not as easily googled. In those questions, the responses are rather in depth and long. So I would like to see whether can I extract some sort of useful data from the numerous comments. Here, I downloaded every comment in the weekly Moronic Monday thread from 10 November 2014 to 18 July 2020 from a total of 296 threads. With that, I have gathered a total of 15,734 comments to analyse.





First thing that I'd like to know is the total number of comments in each weekly thread. So, here I have counted and plotted a figure to illustrate the number of comments since 2014. 

![Weekly no of comments](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-reddit-finance/01%20Weekly%20no%20of%20comments.png)

Two things that you can notice: 
1. There is an obvious upward trend. So it is not a stationary time series data.
1. There is some seasonality pattern to it. The number of comments would peak sometime after the year start then it would go downwards before picking up again in the last quarter of the year.

This would be a good time to dig out my time series knowledge and implement an ARIMA model on this short time series data. I split the small dataset into training set (ranging from 10 Nov 2014 to 31 Dec 2017) and test set (1 Jan 2018 to 18 Jul 2020). I first determined the suitable set of parameters for my ARIMA model based on the training set, which I found to be (3,1,1). This set of parameter yields the lowest AIC score of 1375.784. 

I then developed an ARIMA model on a rolling basis assuming that the set of parameter remains valid. What this means is that for next prediction, I refit my ARIMA model based on the most recent _n_ data points, in this case, _n_ = 164. The prediction made and the 95% confidence interval as well as the actual no of comments are plotted in the figure below. The ARIMA model works well as it is able to capture the seasonality trend and most of the actual no of comments are well within the confidence interval. However, it should be noted the confidence interval is rather large as the standard deviation is about 35. 

![Actual vs predicted no of comments](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-reddit-finance/02%20ARIMA%20model.png)




_xx_ 			- italic
**xx** 			- bold
# xxx			- header
[display text](link)	- hyper link 
[display text][ref] 	[ref]: website
![display text](link)	- images
> text 				- block quote
* text 				- unordered list
    * text 			- unordered sublist
1. text 			- ordered list
