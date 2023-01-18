---
layout: page
title: Hawker centre dashboard # Project post title
# description: a project with a background image # Project post description
img: assets/img/12.jpg # Not necessary to have this image, will be used as thumbnail
# redirect: https://unsplash.com # Insert link if want to redirect to another website, else ignore/remove this.
importance: 1
category: deployment # deployment / predictive / descriptive, if wrong category, the post won't be posted

comments: true
published: true

# - Need to update based on SG time
# - tz-naive vs tz-aware time

---

There was a [post](https://towardsdatascience.com/creating-a-web-application-to-analyse-dengue-cases-1be4a708a533) by Benedict Soh on [tds](https://towardsdatascience.com/) where he was developed and deployed a dashboard to track and analyse dengue cases in Singapore. The tds post was made in late 2020's and I stumbled upon in early 2022. The dengue dashboard would have been of great use if it was more up-to-date with the latest news and tweets about dengue. However, the dashboard was a static app and it did not function properly after 2 Aug 2020.

Back then, I was really interested in learning how to develop and deploy an application, be it a model or a dashboard. The main objective was to learn to deploy whatever I would have built in the future and not simply leave it in one of my many local folders or github repos. Not to mention, the post is rather simple and it would serve as a good base for me to learn how to develop and deploy an app.

## Data.gov.sg search
I did a search on [data.gov.sg](https://data.gov.sg/) to find what intriguing dataset that I could use to develop such dashboard and I found the [hawker centre closure dates dataset](https://data.gov.sg/dataset/dates-of-hawker-centres-closure). Seeing that there are temporal and spatial elements, I decided to use it. With that in mind, the dashboard has 2 main features:

1. A map of Singapore with all the hawker centres indicated as points. Each point should have 1 of 3 colours to indicate its status (open, closing within a month or closed).
1. Two separate tables that show a list of hawker centres that are currently closed and the upcoming closures.

The dashboard is built using the same template as that by Benedict Soh. Full credits to him for building the dashboard, I am simply adapting the codes to his. The dashboard and map are built using `dash` and `folium` respectively. 

## Data API call
In the original tds post, the author was using static data to plot the visualization. I, however, did not use a static data. Rather, I used the data API to fetch the latest data. Of course, this again is a challenge for me because how do I do it? I search through tds again and found this [post](https://towardsdatascience.com/exploring-data-gov-sg-api-725e344048dc) by Tony Ng, who did a brief introduction and mimicking what was done, I managed to get the script to use the API instead. The following command was used to call the data using `requests`:
{% raw %}
```html
import requests

requests.get('https://data.gov.sg/api/action/datastore_search?resource_id=b80cb643-a732-480d-86b5-e03957bc82aa&limit=200').json()
```
{% endraw %}

## Data manipulation
Although the data has been called via API, the data is a json format. I converted it into a pandas dataframe before converting it from a wide to long table. The table is a wide table as each row represents a single unique hawker centre and some columns represent the cleaning or closure date for a particular quarter. Of course, this wide table could be used but I just prefer using a long table for data manipulation. 

Once I got a long table, I then had to identify and extract hawker centres that are currently open today, closing within a month and closing more than a month later. One thing that I have to be careful here is to ensure that all hawker centres should appear once and only once and should be in one of the three lists. The difficulty I had with the data manipulation is the manipulation of datetime. I am not particularly good with it but I found [arrow](https://arrow.readthedocs.io/en/latest/) package. It saved my life! And also, save me from all the hassle :D

Based on the three lists, I colour code the hawker centres into green (currently open), orange (closing soon) and red (currently closed) for the map. Tables are also built accordingly for feature #2. 

Other than that, there is nothing else interesting than to say that I used pandas to manipulate the data.


## Dashboard development 
There is few changes from the original codes by Benedict Soh. I simply replaced the news and social media tabs with the "Currently Closed" and "Upcoming Closure" tabs. Any analysis on the news and tweets were also removed. Within the codes, some of the functions were renamed accordingly so that it seems more intuitive when it comes to reading my own codes. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202209-hawker-dashboard/dashboard.PNG" title="Snapshot of dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This is how the dashboard looked like when I ran it back in Sep 2022. 

## Dashboard deployment
Back in September 2022, I was able to use the free service provided by Heroku. I followed the steps as shared by Benedict to deploy on Heroku though it did take me over 20 runs to troubleshoot the errors. I couldn't remember what I did and it took a while to work but I still got there. 

However, Heroku has decided to remove the free service and would start charging from 28 November 2022 onwards based on this [article](https://techcrunch.com/2022/08/25/heroku-announces-plans-to-eliminate-free-plans-blaming-fraud-and-abuse/). I then had to turn to an alternative platform and I decided to try AWS as it is one of the most popular cloud service providers.

Referencing this [medium post](https://aws.amazon.com/getting-started/guides/deploy-webapp-ec2/), I followed the steps to test out the example provided. The step by step worked well and the app was deployed successfully on AWS Elastic Beanstalk but my app didn't get deployed successfully though. I looked through the log files and found some changes that needed to be done:

1. Updating the packages as some of the packages had deprecated (e.g. I should import `dcc` directly from `dash` instead of importing `dash_core_components` as `dcc`).
1. My app wouldn't work well with the `folium` map and I had to change it to a `plotly` map. The reason being that the `folium` map had to be saved as html before displaying it. I was having trouble dealing with it and I decided to change it to a `plotly` map so that it can be displayed directly.
1. Despite making the above changes, the app still wasn't deployed successfully. After looking through the log files, I found out that it was trying to listen to port `8000` instead of the `8080` as specified. After changing it to port `8000`, the app was finally running.


## Areas of improvement
I would prefer to add in more interactive features where the user may sort the tables according to any of the columns instead of being sorted by date by default.

I would also love to change the background or logo to reflect some Singaporean food. In fact, it would be good if each point within the map could show some famous food or food that are highly rated within that hawker.

Another matter to look at is to allow the dashboard to be updated automatically based on Singapore time. Currently the dashboard doesn't seem to be updated or refreshed. Instead, it is frozen and displayed as it is when it was deployed successfully. I am aware that there are solutions available such as [this](https://stackoverflow.com/questions/65469454/updating-data-used-by-aws-elastic-beanstalk-deployed-webapp). I have yet to take the time to set this up as I realize that I would need to get a good solid foundation of AWS first.
