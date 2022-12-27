---
layout: post
title: Analysis of SGReddit Daily Thread - Part 1
date:   2020-06-15
description: Part of 1 of 3-parts analysis of SGReddit daily threads
tags: [reddit, singapore]
categories: analysis
comments: true
published: true
---

This is part 1 of 3 parts analysis of the [SGreddit][SGreddit] daily threads. The data from 24 Jun 2014 to 2 Jun 2020 were scraped using [PRAW API][PRAW] and this gives me a total of 2166 threads. Though I have to admit that I was supposed to get 2173 threads over 7 threads were missing and couldn't be found on Reddit. The information that I scraped were:
<ul>
  <li>content of the comment</li>
  <li>username of the comment</li>
  <li>time of comment submission</li>
  <li>votes of the comment</li>
</ul> 

I then collated all these information into a huge master csv file. There must be a better way to collate and analyse these huge amount of data _(perhaps json?)_. Anyway, this is my first proper data analysis work. Hopefully I do it some justice and gain some insights.

Before I started any analysis, I first have to do some preprocessing work. The day of the week and week number for each each were extracted. Deleted or removed comments were removed from the data. Thereafter, the analysis is done on the clean dataset.

<hr>

### How has the community of SG daily thread grown over the years?
First thing I want to know is how has the community grown over the years, even before I joined Reddit. One way to track and estimate the growth of the community is to determine the number of daily unique users for the daily thread. No doubt that the same person may have created multiple accounts such as a throwaway account and make a comment on the daily thread but based on my experience, I don't see many throwaway accounts. So this should be a good representation of the community growth.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/No%20of%20unique%20users%20-%20day.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Heatmap of number of daily unique posters from 24 Jun 2014 to 2 Jun 2020.
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="https://github.com/brandonyongys/test/blob/main/img/202006-sg-reddit/Distribution%20of%20upvotes%20for%20the%20year%202017.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Above figure is the number of daily unique posters for each daily thread in a heatmap form. The horizontal axis is the week number of the year and vertical axis is the day of the week with Monday at the top and Sunday at the bottom. As the number of unique posters increases, the intensity of the colour increases based on the colour map on the side, starting from light green up to dark green. The white bars in the heatmap represent the missing data. 

Despite the missing data, you can clearly see that the number of unique posters have been increasing week on week. Besides that, you can see the clear distinction in the number of unique posters on weekday daily threads versus the weekend daily threads. A possible explanation is that more redditors would be online on weekdays due to reasons such as being at work, whereas redditors would be enjoying their lives on the weekends such as going out to the shopping malls or exercising.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/No%20of%20unique%20users%20-%20month%202.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Monthly number of unique posters from 24 Jun 2014 to 2 Jun 2020.
</div>

Besides that, I also plotted the total monthly unique posters as shown in the figure above. The horizontal axis represents the year and the vertical axis is the month. The total number of unique posters for June 2014 and June 2020 are underrepresented as I do not have the full month data. Looking at this figure, you can see that from June 2014 to December 2017, the monthly total unique posters keeps increasing. Starting from January 2018, the monthly total unique posters hovers around 1600 to 1800 and have been that way ever since. 

However, from March 2020, there has been a spike in total monthly unique posters and it reaches its peak of 2152 unique posters in April 2020. This is due to the Covid-19 pandemic that has caused a great impact on the world. Singapore government has encouraged employers to allow employees to work from home whenever possible. On 7 April 2020, circuit breaker was implemented and all non-essential workers were to work from home and all schools were closed. 

<hr>

### How has the comments on SG daily thread grown over the years?
Since there is evidence that the community is growing, how about the number of comments made? Are the community becoming more engaged and chattier?

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/No%20of%20posts%20-%20day.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Heatmap of number of daily posts from 24 Jun 2014 to 2 Jun 2020.
</div>

I have plotted another heatmap for the daily number of comments for each of the daily thread. Likewise, the horizontal axis is the week number of the year and the vertical axis is the day of the week. The colour map is centered about 1000 comments.

You can see a progression of the daily number of posts from a very low value of about 50 to about 1000 posts. There is a very clear separation at the start of 2017, that's when the daily posts approach 1000 posts and start to hover around that value since. However, there was a brief period of time in 2018 for approximately 4 weeks that the daily number of posts reached a very high count of 2000 or more posts. The maximum number of posts back then was about 3281.

Besides that, you can also clearly see that the number of posts on the daily threads during the weekend versus the weekdays is vastly different. During the weekdays, the number of posts hover about 1000 posts for the past 3 years. On the other hand, the number of posts would hover about 600 posts. This can be explained simply because of the reduced number of unique users on the weekends, and hence, reduced engagement.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/No%20of%20posts%20-%20day%20median.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Median number of daily posts from 24 Jun 2014 to 2 Jun 2020.
</div>

We can take a look from a different perspective by plotting the median number of posts for each day of the week by year. I decided to use the median value instead of mean value because of the high count of comments in 2018, which can significantly skew the results. The values for first 3 years (2014 to 2016) should be taken with a pinch of salt as the number of comments back then was still experiencing growth and hasn't reached its stationary stage yet. So simply taking a median value for then period is like taking the mid point of an ever increasing growth.

However, we can take a look at the data since 2017. The median value of each day of the week is rather consistent. The data for 2018 is the highest simply because of the outliers in early 2018 as mentioned previously. Looking at the data for 2020, the median number of posts is still about the same value as the previous year despite the implemented circuit breaker. _Could this mean that the number of posts per user has dropped?_

<hr>

### Have the users been posting more?
I am wondering and checking whether has an average user submitting fewer comments. Here, I calculated the average comments per user by dividing the total comments by the total unique users for each day. Then, I plotted another heatmap to illustrate the average number of comments per user since 2014, as shown below. The colour map is centered about the value 3.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/No%20of%20posts%20per%20user%20-%20day.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Heatmap of number of posts per poster from 24 Jun 2014 to 2 Jun 2020.
</div>

The average number of posts per user back then was about 2 to 3 posts and it has grow up to 3 to 4 posts in recent time. Occasionally the number of posts per user does go up to 5 and beyond. You can see a clear difference in number of posts per user on weekdays versus weekends. Users tend to post about 3 to 4 posts on weekdays and on weekends, they tend to post about 2 to 3. The average user is slightly less chatty because of the reduced number of users that contribute the community engagement.

Looking at the blue bars, which indicate a high number of posts per user, there are two period of time where this happened. First was in end of 2014 and another was in early to mid 2018. In 2014, the users were probably excited about clearing their leaves and school year was going to end, so it was time for them to go on holiday or enjoy their down time. In 2018 though, it was a peculiar period. As indicated previously, this period of time experienced a high number of posts and a high number of users. So this prompts a question - _what was happening back then that caused such a surge in activity?_ 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Median%20no%20of%20posts%20per%20user%20-%20day.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Median number of posts per poster from 24 Jun 2014 to 2 Jun 2020.
</div>

Looking at the heatmap above, the average user in 2020 has posted slightly fewer comments as compared to the median posts per user in 2017 to 2019. This is odd as I would have expected that circuit breaker would have increased the number of users and posts. I suppose that since non-essential workers were working from home for the entire circuit breaker and students were doing home based learning in the first half of circuit breaker and then they were on their June holiday in the second half, so their lives were less happening and they have fewer things to rant or talk about. 

<hr>

### What about the hourly activity of the daily thread?
I decided to use the data for 2019 to calculate and plot the average hourly number of posts for each day of the week. The reason I chose 2019 data is because there doesn't seem to have any outlier data and also because it is the most recent full year data that I have. 

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Hourly%20posts%20-%20average%202019.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hourly average number of posts by day in the full year of 2019.
</div>

You can clearly is that there is an obvious trend regardless of the day of the week. From 6am all the way to 1pm, the number of comments posted is on a downhill trend. Starting from 1pm, the number of posts start to pick up. This is where the trend of weekday and weekend start to diverge. The reason for the sudden drop in activity from 6am to 1pm is because 1) a new daily thread is posted and pinned, replacing the previous day thread and ending all discussions in the previous day thread, and 2) the users are preparing to go to work/school and are focusing on them first.

On weekdays, the number of comments posted would climb faster than it would on a weekend and it would reach it maximum at about 6-7pm. From there, it would very slowly decrease all the way to 6am. Then the cycle repeats. 

The trend for the weekend is a little bit tricky to see. You would have to look at the end from 1pm of either Saturday or Sunday and connect the trend to the following day (Sunday or Monday) to see the actual trend and to ensure continuity. The number of posted comments on the weekend pick up slower and reach it peak at about 9pm. Then it would go down a little bit and from midnight onwards, it would go up to about 50 comments per hour at 6am before it goes downhill again.  

One thing to note is that on Thursday between 4 to 7pm, the number of comments posted for each hour of the 3 hours time frame is significantly higher than the usual count for a weekday (70 comments vs 60 comments respectively). _Is this because everyone is excited about TGIF the following day?_

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/Hourly%20posts%20-%20average%20CB.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Hourly average number of posts by day during circuit breaker 2020.
</div>

I've also plotted the average hourly comments for the ciruit breaker period as well. The shape is generally the same as last year's average hourly comments. However, there are a few notable changes.

The first difference is that there is almost no difference between weekdays and weekend comments especially in the first half of the day. Between 12 to 6am, there was a maximum difference of 20-30 comments for weekday versus weekend comments and it would slowly converge to about 50 comments at 6am. However, during the ciruit breaker, there is almost no difference. The second half of the day, there is still some difference but the difference between weekday and weekend comments are about 10 comments for each hour compared to last year's difference of about 20 comments.

The second difference is that the maximum hourly comments in the first half of the day tend to be lower than the second half of the day. However, that trend is no longer valid as the maximum for the first half and second half are the same, which is about 80 comments. 

Although the hourly comments at 6am is still about 50 comments, the decline in hourly comments have significantly slowed down. For example, in last year's trend, the hourly comments at 8am was about 20 comments but during the circuit breaker period, the comments posted at 8am was nearly double of that (approximately 40 comments).

Another difference is the night activity would slowly die down after a certain hour last year. During circuit breaker, the hourly activity at night didn't die down. Rather, it was stable and sometimes would increase.

All these differences show that circuit breaker has indeed changed the behaviour of the sg redditors. As they couldn't go out and enjoy activities such as dating and shopping, more redditors have spent more time online and engaged with others within the community although the average redditor has posted fewer comments.

That is all for the part 1 of my analysis. Stay tuned for more analysis!

[SGreddit]: https://www.reddit.com/r/singapore/
[PRAW]: https://praw.readthedocs.io/en/latest/
