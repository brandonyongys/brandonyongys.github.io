---
layout: post
title: Analysis of Reddit Singapore Daily Thread - Part 3
tags: [reddit]
comments: true
published: true
---

A personal interest of mine and also one of the main objective in my life ins to achieve financial independence. Like how there is a dedicated sub for the Singapore community and people into finance, there is also a dedicated sub for people who are into financial independence. As before, I am going to learn and data mine the weekly "Help me FIRE!" thread on [/r/financialindependence](https://old.reddit.com/r/financialindependence/). In total, I have extracted the comments in the weekly thread dated from 4th March 2019 to 20th July 2020. The latest pinned thread dated 27th July 2020 is not considered as it just begun when I first started my work on it. With that, I have a total of 10,212 comments to work with.

The sub moderator has shared some guideline on what to share when ask for help in the weekly thread, which are:
1. Introduce yourself
1. Age / Industry / Location
1. General goals
1. Target FIRE Age / Amount / Withdrawal Rate / Location
1. Educational background and plans
1. Career situation and plans
1. Current and future income breakdown, including one-time events
1. Budget breakdown
1. Asset breakdown, including home, cars, etc.
1. Debt breakdown
1. Health concerns
1. Family: current situation / future plans / special needs / elderly parents

## Let's take a look of the comments on the surface level
![weekly no of comments](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-finance-FIRE/00%20Weekly%20no%20of%20comments.png)

There is hardly any growth in terms of number of comments in each weekly thread. There is no obvious upwards or downwards trend. Instead, it is rather stagnant as it would usually fluctuates between 50 to 250 comments with an average of 133 comments. The low comments count in the 1st July 2019 thread is due to lack of questions by others.

![No of words](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-finance-FIRE/03%20Boxplot%20no%20of%20words.png)

As for the number of words, the comment is typically 400 words or less, excluding any quotes. This is consistent with the need that the user, especially those who are seeking for advice, would need to provide quite an elaborate details of themselves and their financial matters.


## What is the background of the people who usually ask for help?


From this, I'd try to mine the data from the somewhat structured yet unstructured comments to profile the community that are pursuing financial independence. First thing that I have to do is to all the deleted or removed comments. I then removed the quotes within the remaining comments as it can lead me to double count instead. After messing around with regular expression and doing my best, below are some of the profiles I managed to extract.

### Age group
![Age distribution](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202008-finance-FIRE/01%20Age%20distribution.png)

Most of the users that are seeking for FIRE advice are typically from pre 20s to 30s with the 20s as the major age class. This is not too surprising since it would be much easier to achieve their FIRE goal if they were to start their FIRE journey early. There are still a group of users who are within their 40s and 50s and are seeking help to FIRE. There are not a lof them but still, some of them may need help as they are still struggling to do so. I am happy for them to speak up and ask for advice instead going down their original path. Better late than never :).


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
