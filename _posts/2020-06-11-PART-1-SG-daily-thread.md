---
layout: post
title: Analysis of Reddit Singapore Daily Thread - Part 1
tags: [reddit]
comments: true
published: true
---

This is part 1 of the series on the analysis of the [SGreddit][SGreddit] daily thread. I scraped the daily threads from 24th June 2014 up to 2nd June 2020 using the [PRAW API][PRAW], giving me a total of 2166 threads. Though I have to admit that I was supposed to crawl 2173 daily threads but 7 threads were missing and couldn't be found on Reddit.

The information thaw I scraped are : 
  1. content of the comment  
  2. username of the comment
  3. time of comment submission
  4. votes of the comment

I then collated all the information into a huge csv file and used it as the master file for my analysis. Though I should research more on what is the more appropriate method to store all these information _(json or csv or is there a better option?)_. Anyway, below is my initial analysis of the daily threads over the years, primarily focused on the basic descriptive information.

### How has the community of SG daily thread grown over the years?
|[No of daily unique posters](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202006-sg-reddit/No%20of%20unique%20users%20-%20day.png)

Above figure is the number of daily unique users for each of the daily thread. The horizontal axis is the week number of the year and vertical axis is the day of the week with Monday at the top and Sunday at the bottom. As the number of unique users increases, the intensity of the colour changes from light green to dark green. The white bars represent the missing data. 

Despite the missing data, you can clearly see that the day on day number of unique users have been increasing. Besides that, you can see the clear distinction in the number of unique users on weekday daily threads versus the weekend daily threads. This shows that on weekdays, more redditors would be online such as being at work whereas on weekends, redditors would be doing more work offline such as going out to the shopping malls.

![No of monthly unique posters](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20unique%20users%20-%20month%202.png?raw=true)

We can also take a look at the total number of unique users on the daily thread for each month. In the above figure, the horizontal axis represents the year and the vertical axis is the month. The number of unique users for June 2014 is underrepresented as I do not have the data for the full month. 

Looking at this figure, you can see that from 2014 to 2017, the monthly total unique posters keeps increasing. In 2018, the monthly total unique posters hovers around 1600 to 1800 and have been that way since. However, in 2020, there is a spike in total unique users starting from March with a maximum of 2152 unique users in April. This is due to the Covid-19 pandemic that has caused a great impact on the world. Singapore government has encouraged employers to allow employees to work from home whenever possible. On 7 April 2020, circuit breaker was implemented and all non-essential workers were to work from home and all schools were closed. 



[SGreddit]: https://www.reddit.com/r/singapore/
[PRAW]: https://praw.readthedocs.io/en/latest/

