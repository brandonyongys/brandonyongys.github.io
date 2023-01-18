---
layout: page
title: SGReddit analysis # Project post title
# description: a project with a background image # Project post description
img: assets/img/12.jpg # Not necessary to have this image, will be used as thumbnail
# redirect: https://unsplash.com # Insert link if want to redirect to another website, else ignore/remove this.
importance: 1
category: descriptive # deployment / predictive / descriptive, if wrong category, the post won't be posted

comments: true
published: true

---

This descriptive project revolves around SGReddit daily threads. The primary python packages used are [PRAW API][PRAW] and pandas. The data covers from 24 Jun 2014 to 2 Jun 2020, which gives me a total of 2166 threads. 7 threads were missing and couldn't be found on SGReddit despite the manual search. The information that I scraped were:
<ul>
  <li>content of the comment</li>
  <li>username of the comment</li>
  <li>time of comment submission</li>
  <li>votes of the comment</li>
</ul> 


The data were then collated into a large master csv file though there must be better and more efficient way to store and read these data _(perhaps json?)_. Anyway, this is my first attempt at a proper data analysis work. Hopefully I do it some justice and gain some insights.

Although I've only collected 4 information, these information can be used to answer a number of things.

<hr>

### How has the community of SGReddit grown over the years?
First thing I want to know is how has the community grown over the years, even before I joined Reddit. One way to track and estimate the growth of the community is to determine the number of daily unique users for the daily thread. No doubt that the same person may have created multiple accounts such as a throwaway account and make a comment on the daily thread but based on my experience, I don't see many throwaway accounts. So this should be a good representation of the community growth.

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/No%20of%20unique%20users%20-%20day.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Heatmap of number of daily unique posters from 24 Jun 2014 to 2 Jun 2020, group by day of the week. As the number of unique posters increases, the intensity of the colour increases based on the colour map on the side, starting from light green up to dark green. Solid white lines represent the missing threads.
</div>

Despite the missing data, you can clearly observe a few things:
1. The number of unique posters increases across the years for any given day of the week as indicated by the increased intensity of the colour.
1. There is a clear distinction in the number of unique posters before 2017 and 2017 onwards, as indicated by the lighter vs darker green. This may be when Reddit really kicked off in Singapore and garnered more users.
1. There is also a clear distinction in the number of unique posters in the weekdays vs the weekends across the years. A possible explanation is that more redditors would be online on weekdays due to reasons such as being at work, whereas redditors would be enjoying their lives on the weekends such as going out to the shopping malls or exercising. 



<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/No%20of%20unique%20users%20-%20month%202.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Monthly number of unique posters from 24 Jun 2014 to 2 Jun 2020. The total number of unique posters for June 2014 and June 2020 are underrepresented as I do not have the full month data.
</div>

Based on this figure, you can see that from June 2014 to December 2017, the monthly total unique posters keeps increasing. Starting from January 2018, the monthly total unique posters hovers around 1600 to 1800 and have been that way ever since. 

However, from March 2020, there has been a spike in total monthly unique posters and it reaches its peak of 2152 unique posters in April 2020. This is due to the Covid-19 pandemic that has caused a great impact on the world. Singapore government has encouraged employers to allow employees to work from home whenever possible. On 7 April 2020, circuit breaker was implemented and all non-essential workers were to work from home and all schools were closed. 



<hr>

### How has the number of comments grown over the years?
Since there is evidence that the community is growing, how about the number of submitted comments? Are the community becoming more engaged and chattier?

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202006-sg-reddit/No%20of%20posts%20-%20day.png" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Heatmap of number of daily posts from 24 Jun 2014 to 2 Jun 2020, group by the day of the week. The colour map is centered about 1000 comments.
</div>

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
