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
![No of daily unique posters](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202006-sg-reddit/No%20of%20unique%20users%20-%20day.png)

Above figure is the number of daily unique users for each of the daily thread. The horizontal axis is the week number of the year and vertical axis is the day of the week with Monday at the top and Sunday at the bottom. As the number of unique users increases, the intensity of the colour changes from light green to dark green. The white bars represent the missing data. 

Despite the missing data, you can clearly see that the day on day number of unique users have been increasing. Besides that, you can see the clear distinction in the number of unique users on weekday daily threads versus the weekend daily threads. This shows that on weekdays, more redditors would be online such as being at work whereas on weekends, redditors would be doing more work offline such as going out to the shopping malls.

![No of monthly unique posters](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20unique%20users%20-%20month%202.png?raw=true)

We can also take a look at the total number of unique users on the daily thread for each month. In the above figure, the horizontal axis represents the year and the vertical axis is the month. The number of unique users for June 2014 is underrepresented as I do not have the data for the full month. 

Looking at this figure, you can see that from 2014 to 2017, the monthly total unique posters keeps increasing. In 2018, the monthly total unique posters hovers around 1600 to 1800 and have been that way since. However, in 2020, there is a spike in total unique users starting from March with a maximum of 2152 unique users in April. This is due to the Covid-19 pandemic that has caused a great impact on the world. Singapore government has encouraged employers to allow employees to work from home whenever possible. On 7 April 2020, circuit breaker was implemented and all non-essential workers were to work from home and all schools were closed. 

### How has the comments on SG daily thread grown over the years?
![No of daily posts](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20posts%20-%20day.png?raw=true)

Above is another heatmap for the number of posts for each of the daily thread. Likewise, the horizontal axis is the week number of the year and the vertical axis is the day of the week. The white bars represent missing data. The colour map is centered about 1000 posts. 

You can see a very progression of the daily number of posts from a very low value of about 50 to about 1000 posts. There is a very clear separation at the start of 2017. That's when the daily posts approach 1000 posts and start to hover around that value since. However, there was a brief period of time in 2018 (approximately 4 weeks) that the daily number of posts reached a very high count of 2000 or more posts. The maximum number of posts back then was about 3281.

Besides that, you can also clearly see that the number of posts on the daily threads during the weekend versus the weekdays is vastly different. During the weekdays, the number of posts hover about 1000 posts for the past 3 years. On the other hand, the number of posts would hover about 600 posts. This can be explained simply because of the reduced number of unique users on the weekends.

![Median daily posts](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20posts%20-%20day%20median.png?raw=true)


We can take a look at the above figure which shows the median number of posts for each day of the week by year. I decided to use median instead of mean because of the high count of posts in 2018, which can be considered as outliers. The values for first 3 years (2014 to 2016) should be taken with a pinch of salt as the number of posts back then was still experiencing growth and hasn't reached its stationary stage yet. So simply taking a median value for then period is liken to taking the mid point of an ever increasing growth.

However, we can take a look at the data since 2017. The median value of each day of the week is rather consistent with little variance. The data for 2018 is the highest simply because of the outliers in early 2018 as mentioned previously. Looking at the data for 2020, the median number of posts is still about the same value as the previous year despite the implemented circuit breaker. _Could this mean that the number of posts per user has dropped?_

### Have the users been posting more?
![Daily posts per user](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/No%20of%20posts%20per%20user%20-%20day.png?raw=true)
Above is the number of psots per user for each daily thread since 2014. The average number of posts per user back then was about 2 to 3 posts and it has grow up to 3 to 4 posts in recent time. Occasionally the number of posts per user does go up to 5 and beyond. You can see a clear difference in number of posts per user on weekdays versus weekends. Users tend to post about 3 to 4 posts on weekdays and on weekends, they tend to post about 3 to 4. This is very likely due to fewer engagements as users are enjoying their life offline.

Looking at the blue bars, which indicate a high number of posts per user, there are two period of time where this happened. First was in end of 2014 and another was in early to mid 2018. In 2014, the users were probably excited about clearing their leaves and school year was going to end, so it was time for them to go on holiday or enjoy their down time. In 2018 though, it was a peculiar period. As indicated previously, this period of time experienced a high number of posts and a high number of users. So this prompts a question - _what was happening back then that caused such a surge in activity?_ 

![Median daily posts per user](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Median%20no%20of%20posts%20per%20user%20-%20day.png?raw=true)
Looking at the heatmap above, the average user in 2020 has posted slightly fewer comments as compared to the median posts per user in 2017 to 2019. This is odd as I would have expected that circuit breaker would have increased the number of users and posts. I suppose that since non-essential workers were working from home and students were doing home based learning for the first half of circuit breaker and were on their June holiday in the second half. So their lives were less happening and they have fewer things to rant or talk about. 


### What about the hourly activity of the daily thread?
I decided to use the data for 2019 to calculate and plot the average hourly number of posts for each day of the week. The reason I chose 2019 data is because there doesn't seem to have any outlier data and also because it is the most recent full year data that I have. 

![Hourly posts](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Hourly%20posts%20-%20average%202019.png?raw=true)
You can clearly is that there is an obvious trend regardless of the day of the week. From 6am all the way to 1pm, the number of comments posted is on a downhill trend. Starting from 1pm, the number of posts start to pick up. This is where the trend of weekday and weekend start to diverge. 

On weekdays, the number of comments posted would climb faster than it would on a weekend and it would reach it maximum at about 6-7pm. From there, it would very slowly decrease all the way to 6am. Then the cycle repeats. 

The trend for the weekend is a little bit tricky to see. You would have to look at the end from 1pm of either Saturday or Sunday and connect the trend to the following day (Sunday or Monday) to see the actual trend and to ensure continuity. The number of posted comments on the weekend pick up slower and reach it peak at about 9pm. Then it would go down a little bit and from midnight onwards, it would go up to about 50 comments per hour at 6am before it goes downhill again.  

One thing to note is that on Thursday between 4 to 7pm, the number of comments posted for each hour of the 3 hours time frame is significantly higher than the usual count for a weekday (70 comments vs 60 comments respectively). _Is this because everyone is excited about TGIF the following day?_

![Hourly posts during CB](https://github.com/brandonyongys/brandonyongys.github.io/blob/master/img/202006-sg-reddit/Hourly%20posts%20-%20average%20CB.png?raw=true)
I've also plotted the average hourly comments for the ciruit breaker period as well. The shape is generally the same as last year's average hourly comments. However, there are a few notable changes.

The first difference is that there is almost no difference between weekdays and weekend comments especially in the first half of the day. Between 12 to 6am, there was a maximum difference of 20-30 comments for weekday versus weekend comments and it would slowly converge to about 50 comments at 6am. However, during the ciruit breaker, there is almost no difference. The second half of the day, there is still some difference but the difference between weekday and weekend comments are about 10 comments for each hour compared to last year's difference of about 20 comments.

The second difference is that the maximum hourly comments in the first half of the day tend to be lower than the second half of the day. However, that trend is no longer valid as the maximum for the first half and second half are the same, which is about 80 comments. 

Although the hourly comments at 6am is still about 50 comments, the decline in hourly comments have significantly slowed down. For example, in last year's trend, the hourly comments at 8am was about 20 comments but during the circuit breaker period, the comments posted at 8am was nearly double of that (approximately 40 comments).

Another difference is the night activity would slowly die down after a certain hour last year. During circuit breaker, the hourly activity at night didn't die down. Rather, it was stable and sometimes would increase.

All these differences show that circuit breaker has indeed changed the behaviour of the sg redditors. As they couldn't go out and enjoy activities such as dating and shopping, more redditors have spent more time online and engaged with others within the community although the average redditor has posted fewer comments.

That is all for the part 1 of my analysis. Stay tuned for more analysis!

[SGreddit]: https://www.reddit.com/r/singapore/
[PRAW]: https://praw.readthedocs.io/en/latest/
