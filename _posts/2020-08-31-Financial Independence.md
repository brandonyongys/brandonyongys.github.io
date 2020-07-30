---
layout: post
title: Financial independence
tags: [reddit]
comments: true
published: true
---

A personal interest of mine and also one of the main objective in my life ins to achieve financial independence. Like how there is a dedicated sub for the Singapore community and people into finance, there is also a dedicated sub for people who are into financial independence. As before, I am going to learn and data mine the weekly "Help me FIRE!" thread on [/r/financialindependence](https://old.reddit.com/r/financialindependence/). In total, I have crawled the comments in the weekly thread dated from 4th March 2019 to 20th July 2020 using the [PRAW API](https://praw.readthedocs.io/en/latest/). The latest pinned thread that started on 27th July 2020 is excluded from my analysis as it has just begun when I first started my analysis. For that 1 year and 5 months worth of data, I have a total of 10,212 comments to work with.

In the weekly thread, the sub moderator has shared some guideline on what to share when asking for help/advice. The posters would typically give a brief introduction such as age, industry and location, and more specific personal finance related details such as FIRE milestones and expenditure breakdown.

## First, let's take a look at comments on a high level
![weekly no of comments](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-finance-FIRE/00%20Weekly%20no%20of%20comments.png)

First I would want to look at is the number of comments in each weekly thread. There is hardly any growth in terms of number of comments in each weekly thread. There is no obvious upwards or downwards trend. Instead, it is rather stagnant as it would normally fluctuates between 50 to 250 comments with an average of 133 comments. The low comments count in the 1st July 2019 thread is due to lack of questions by others.

![No of words](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-finance-FIRE/03%20Boxplot%20no%20of%20words.png)

As for the number of words, the comment is typically 400 words or less, excluding any quotes. The comments with 400 words or more are usually the comments from the people who are seeking for advice, as they are doing their best to provide as much information as needed so that they could get as much advice and help as possible. On the other hand, the comments with 400 words or less are usually the responses to the original poster. 

## What is the background of the people who usually ask for help?
Given the information that needed to be shared, I'd try to give some profile from the somewhat structured yet unstructured data. First, I have to clean up my data by removing all the deleted or removed comments. I then removed the quotes within the comments as it can lead me to double count instead. After messing around with regular expression and doing my best, below are some of the profiles I managed to extract.

### Age group
![Age distribution](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-finance-FIRE/01%20Age%20distribution.png)

Most of the users that are seeking for FIRE advice are in their 20s and 30s. This is not too surprising since it would be much easier to achieve their FIRE goals if they were to begin earlier. There are still a group of users who are within their 40s and 50s and are seeking help to FIRE. Although it's not a lot, these older people still need some help as they may be struggling to pay of certain debts or seeking advice on how to speed up their FIRE. I am happy for them to speak up and ask for advice instead continuing down their original path. Better late than never :).

This distribution shows very clearly how financially responsible the younger generations are as they are seeking ways to reduce their financial burden and setting up for their _(future)_ kids. Although there are materials online that the younger generations could have found and read, they may be very much overwhelmed by the vast information and need specific suggestions or opinions instead of a one size fits all solution.

### Location of users




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
