---
layout: page
title: Hawker centre dashboard # Project post title
img: https://danielfooddiary.com/wp-content/uploads/2019/08/Hawkercentre-scaled.jpg 
importance: 1
category: deployment # deployment / predictive / descriptive, if wrong category, the post won't be posted

comments: true
published: true

# - Need to update based on SG time
# - tz-naive vs tz-aware time

---

There was a [post](https://towardsdatascience.com/creating-a-web-application-to-analyse-dengue-cases-1be4a708a533) by Benedict Soh on [tds](https://towardsdatascience.com/) where he developed and deployed a dashboard to track and analyse dengue cases in Singapore. However, the dashboard was a static app and it did not function properly after 2 Aug 2020. It would have been of great use to the Singapore community if it was up-to-date with the latest news and tweets about dengue.

Back then when I stumbled upon it in early 2022, I was interested in learning how to develop and deploy an application, be it a model or a dashboard. The main objective was simply to learn the deployment techniques, which would be useful for anything that I would have built. That would deliver more value than to simply leave the apps in one of my many local folders or github repos. Not to mention, the tds post was rather simple and serve a rather good introduction for me given my lack of knowledge and skills.

# Data.gov.sg search
I searched through [data.gov.sg](https://data.gov.sg/) and found the [hawker centre closure dates dataset](https://data.gov.sg/dataset/dates-of-hawker-centres-closure). There are temporal and spatial elements in the dataset and I could foresee 2 main features in my dashboard:
1. A map of Singapore with all the hawker centres indicated as points. Each point would be 1 of 3 colours to reflect its current status - open, closing within a month or closed.
1. Two separate tables that show a list of hawker centres that are currently closed and the upcoming closures.

The dashboard was built in the similar fashion as that by Benedict Soh. Full credits to him for building the dashboard as I am simply adapting his codes to my dashboard. The dashboard and map were built using `dash` and `folium` respectively.

**EDIT:** The map was subsequently replaced with `plotly`.

# Data API call
In the original post, the author was using static data to plot the visualization. However, I did the opposite and wanted to use the latest dataset. I utilized the data API to fetch the latest data. This [post](https://towardsdatascience.com/exploring-data-gov-sg-api-725e344048dc) by Tony Ng did a great job of providing a high level introduction of the data.gov.sg API and I adapted his work to my work again. For the benefits of others, the following command was used to call the data using `requests`:
{% raw %}
```html
import requests

requests.get('https://data.gov.sg/api/action/datastore_search?resource_id=b80cb643-a732-480d-86b5-e03957bc82aa&limit=200').json()
```
{% endraw %}

To use the above command, go to your desired data.gov.sg dataset and click on the "Data API" button at the top right, if any. Copy the query example link and simply remove the last term ('&limit=5') or you could simply change it to a larger number like what I did in the above.

# Data manipulation
Although the data has been called via API, the data is a json format. I converted it into a simple `pandas` dataframe. The dataframe is is a wide table as each row represents a single unique hawker centre and some columns represent the cleaning or closure date for a particular quarter. I further processed it to be a long table where each row represents a particular hawker centre and closure period. The conversion from wide to long table was done as I preferred using a long table for data manipulation.

I then manipulated the long table to identify and extract 3 tables of hawker centres. The 3 tables contain hawker centres that are currently open, closing within a month and currently closed respectively. I had to take the precaution step to ensure that all hawker centres are accounted for and each hawker centre be in one of the 3 tables. Based on these 3 tables, the hawker centres were then colour coded as green (currently open), orange (closing within a month) and red (currently closed).

The main difficulty I had with the data manipulation is the manipulation of datetime. I am not particularly good with it but I found [arrow](https://arrow.readthedocs.io/en/latest/) package. It saved my life! And also, save me from all the hassle :D


# Dashboard development 
There are a few changes from the original codes by Benedict Soh. I replaced the news and social media tabs with the "Currently Closed" and "Upcoming Closure" tabs. Any analysis on the news and tweets were also removed. Within the codes, some of the functions were renamed accordingly so that it is more intuitive when it comes to reading the codes. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202209-hawker-dashboard/dashboard.PNG" title="Snapshot of dashboard" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

This is how the dashboard looked like when I ran it back in Sep 2022. 

# Dashboard deployment
Back in September 2022, I was able to use the free service provided by Heroku. I followed the steps as shared by Benedict to deploy on Heroku though it did take me over 20 runs to troubleshoot the errors. I couldn't remember what I did and it took a while to work but I still got there. 

However, Heroku has decided to remove the free service and would start charging from 28 November 2022 onwards ([article](https://techcrunch.com/2022/08/25/heroku-announces-plans-to-eliminate-free-plans-blaming-fraud-and-abuse/)). I then had to turn to an alternative platform and I decided to try AWS as it is one of the most popular cloud service providers. I decided to deploy using AWS Elastic Beanstalk as there is a step by step [medium post](https://austinlasseter.medium.com/deploying-a-dash-app-with-elastic-beanstalk-console-27a834ebe91d) by Austin Lassseter.

I tested out the step by step using the provided example and the app was successfully deployed on AWS Elastic Beanstalk. However, when I tried the same set of steps with my app, it was not deployed successfully. I looked through the log files and found some changes that needed to be done:

1. Some of the packages had to be updated as they had deprecated (e.g. I should import `dcc` directly from `dash` instead of importing `dash_core_components` as `dcc`).
1. My app wouldn't work well with the `folium` map as the map would be saved first as html file before being called back for visualization. I changed it to a `plotly` map. 
1. Despite making the above changes, the app still wasn't deployed successfully. After looking through the log files, I found out that it was trying to listen to port `8000` instead of the `8080` as specified. After changing it to port `8000`, the app was finally running.


# Areas of improvement
I would prefer to add in more interactive features where the user may sort the tables according to any of the columns instead of being sorted by date by default.

I would also love to change the background or logo to reflect some Singaporean food. In fact, it would be good if each point within the map could show some famous food or food that are highly rated within that hawker.

Another matter to look at is to allow the dashboard to be updated automatically based on Singapore time. Currently the dashboard doesn't seem to be updated or refreshed. Instead, it is frozen and displayed as it is when it was deployed successfully. I am aware that there are solutions available such as [this](https://stackoverflow.com/questions/65469454/updating-data-used-by-aws-elastic-beanstalk-deployed-webapp). I have yet to take the time to set this up as I realize that I would need to get a good solid foundation of AWS first.
