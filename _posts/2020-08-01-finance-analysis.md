---
layout: post
title: Moronic Monday at the Finance sub
tags: [reddit]
comments: true
published: true
---

Every Monday at the [Finance sub](https://old.reddit.com/r/finance/), a new thread will be posted to allow the community to ask questions anything about finance such as financial careers, homework problems and finance in general. Some of the questions asked may be quite simple and could be easily googled and others are not as easily googled. In those questions, the responses are rather in depth and long. So I would like to see whether can I extract some sort of useful data from the numerous comments. Here, I downloaded every comment in the weekly Moronic Monday thread from 10 November 2014 to 18 July 2020 from a total of 296 threads. With that, I have gathered a total of 15,734 comments to analyse.

## Can I predict next week's total comment counts?
First thing that I'd like to know is the total number of comments in each weekly thread. So, here I have counted and plotted a figure to illustrate the number of comments since 2014. 

![Weekly no of comments](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-reddit-finance/01%20Weekly%20no%20of%20comments.png)

Two things that you can notice: 
1. There is an obvious upward trend. So it is not a stationary time series data.
1. There is some seasonality pattern to it. The number of comments would peak sometime after the year start then it would go downwards before picking up again in the last quarter of the year.

This would be a good time to dig out my time series knowledge and implement an ARIMA model on this short time series data. I split the small dataset into training set (from 10 Nov 2014 to 31 Dec 2017) and test set (1 Jan 2018 to 18 Jul 2020). I first determined the suitable set of parameters for my ARIMA model based on the training set, which I found to be (3,1,1). This set of parameter yields the lowest AIC score of 1375.784. 

I then developed an ARIMA model on a rolling basis assuming that the set of parameter remains valid. What this means is that for next prediction, I refit my ARIMA model based on the most recent _n_ data points, in this case, _n_ = 164. The prediction made and the 95% confidence interval as well as the actual no of comments are plotted in the figure below. The ARIMA model works well as it is able to capture the seasonality trend and most of the actual no of comments are well within the confidence interval. Not to mention, a small dataset is more than sufficient to predict the next week's no of comments, which keeps the training time short.

![Actual vs predicted no of comments](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-reddit-finance/02%20ARIMA%20model.png)

However, it should be noted the confidence interval is rather large as the standard deviation is about 35. Since this is a finance thread for Reddit users to ask questions, they could be asking questions related to recent actions taken by some financial institutions or the impacts of some regional or global events such as the ongoing Covid-19 pandemic. A more accurate model could be built if such information can be incorporated. 


## How lengthy are the comments?
The second thing I'm looking at is the number of words in the comments, which indicates how lengthy each comment is. I first preprocessed the data by removing ny deleted or removed comments as well as comments with no content such as an emoji response. Any URL are replaced with the term "URL" to ease the preprocessing. Besides that, I also removed any quotes the poster may have made within the comment as I would like to see new content rather than repeated contents.

![Boxplot of no of words](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-reddit-finance/03%20Boxplot%20no%20of%20words.png)

The range of words for each comment doesn't change much throughout the years as a poster would typically write 120 or fewer words per comment, excluding any emoji or no content comments. However, there are still a number of comments in each weekly thread that are considered as outliers. Let's take a look at these comments. For this, I will just consider comments with more than 120 words for simplicity sake.

## What are the typically discussed in the weekly thread?
To answer this, I would plot a word cloud with the font size of the terms representing the frequency of the term used. First, I would remove all the stop words in the comments. I have also removed any url and emails within the comments. After cleaning up the text data, the bigram and trigram word cloud are plotted as below:


![Bigram for all comments](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-reddit-finance/05%20Bigram%20for%20all%20comments.png)
![Trigram for all comments](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-reddit-finance/05%20Trigram%20for%20all%20comments.png)

There is nothing surprising here. Most of the terms used are related to finance. In the bigram word cloud, the font size of the different terms are about the same, which indicates that these frequently used terms are used at approximately the same frequency. However, when we look at the trigram, we can see that only a few 3-words terms are frequently used, which are future/free cash flow, some sort of rates such as the risk free rate and federal fund rate.  

Based on these two word clouds, we could conclude that the discussions often revolves around the impact of cash flow and rates on investment such as stock price and stock market. Not to mention, there is a huge emphasis on time value of money. I guess that that huge emphasis is necessary since anyone that asks a question here is often new to finance topic.


## What are the typical terms used in the comments?
![Boxplot of upvotes](link)

Here, I plotted a boxplot for each weekly thread to illustrate the distribution of upvotes. I excluded comments with 1 upvote because a posted comment would come with 1 upvote by default. Of course there would be possibility that the net upvote is equal to 1 but I'd assume that that probability is very low. 

It's quite clear that a typical comment in the Moronic Monday would often receive upvotes than downvotes. People would typically give an upvote if they agree with the stated comment in general or the original poster is asking a question that they too would have asked but afraid to do so. You can see that it's typically 1 to 3 people who like the comment. 

You can see that there are a lot of comments with upvotes thaat are considered as outliers. Almost all comments that received at least 1 downvote are considered as outliers. As for the comments that received upvotes, it is usually those with at least 4 upvotes are considered as outliers. Let's take a look at bigrams and trigrams that often appear in comments with at least 4 upvotes and 1 downvote respectively.



Before constructing the bigrams and trigrams, I first have to remove any url and stopwords such as "the", "those" etc that do not add value or context. 
![Bigram for upvotes comments](link)
![Trigram for upvotes comments](link)

Based on the bigram, the users would often discuss about interest rate, stock market and the financial statements of a company such as cash flow and balance sheet. Based on the trigram, we can observe that the discussions seem to gear more towards the impact of the different matters in the stock market such as the fed interest rate and free cash flow. These can impact how one could evaluate a financial asset and determine whether it is a good investment.

![Bigram for downvotes comments](link)
![Trigram for downvotes comments](link)

Looking at the bigram and trigram for comments with at least 1 downvote, one can get the general sense that the community is not in favour credit card debts, making fast cash or things that can easily googled.





## Can I predict how many upvotes a comment may receive?






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
