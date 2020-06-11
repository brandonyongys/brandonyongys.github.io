---
layout: post
title: Analysis of Reddit Singapore Daily Thread - Part 1
tags: [reddit]
comments: true
published: true
---

This is part 1 of the series on the analysis of the [SGreddit][SGreddit] daily thread. I scraped the daily threads from 24th June 2014 up to 2nd June 2020 using the [PRAW API][PRAW], giving me a total of 2166 threads. Though I have to admit that I was supposed to crawl 2173 daily threads but 7 threads were missing and couldn't be found on Reddit.

The information thaw I scraped are : 
1) content of the comment  
2) username of the comment
3) time of comment submission
4) votes of the comment

I then collated all the information into a huge csv file and used it as the master file for my analysis. Though I should research more on what is the more appropriate method to store all these information (json or csv or is there a better option?).




[SGreddit]: https://www.reddit.com/r/singapore/
[PRAW]: https://praw.readthedocs.io/en/latest/

