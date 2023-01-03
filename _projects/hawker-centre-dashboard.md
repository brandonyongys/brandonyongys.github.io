---
layout: page
title: project 1 # Project post title
description: a project with a background image # Project post description
img: assets/img/12.jpg # Not necessary to have this image, will be used as thumbnail
redirect: https://unsplash.com # Insert link if want to redirect to another website, else ignore/remove this.
importance: 1
category: deployment # deployment / predictive / descriptive, if wrong category, the post won't be posted

comments: true
published: true
---

There was a [post](https://towardsdatascience.com/creating-a-web-application-to-analyse-dengue-cases-1be4a708a533) by Benedict Soh on [tds](https://towardsdatascience.com/) where he was developed and deployed a dashboard to track and analyse dengue cases in Singapore. The tds post was made in late 2020's and I stumbled upon in early 2022. The dengue dashboard would have been of great use if it was more up-to-date with the latest news and tweets about dengue. However, the dashboard was a static app and it did not function properly after 2 Aug 2020.

Back then, I was really interested in learning how to develop and deploy an application, be it a model or a dashboard. The main objective was to learn to deploy whatever I would have built in the future and not simply leave it in one of my many local folders or github repos. Not to mention, the post is rather simple and it would serve as a good base for me to learn how to develop and deploy an app.


# Hawker centre dashboard
I did a search on [data.gov.sg](https://data.gov.sg/) to find what intriguing dataset that I could use to develop such dashboard and I found the [hawker centre closure dates dataset](https://data.gov.sg/dataset/dates-of-hawker-centres-closure). Seeing that there are temporal and spatial elements, I decided to use it. With that in mind, the dashboard has 2 main features:

1. A map of Singapore with all the hawker centres indicated as points. Each point should have 1 of 3 colours to indicate its status (open, closing within a month or closed).
1. Two separate tables that show a list of hawker centres that are currently closed and the upcoming closures.

# Data API call
In the original tds post, the author was using static data to plot the visualization. I, however, did not use a static data. Rather, I used the data API to fetch the latest data. Of course, this again is a challenge for me because how do I do it? I search through tds again and found this [post](https://towardsdatascience.com/exploring-data-gov-sg-api-725e344048dc) by Tony Ng, who did a brief introduction and mimicking what was done, I managed to get the script to use the API instead. The following command was used to call the data using `requests`:
{% raw %}
```html
import requests

requests.get('https://data.gov.sg/api/action/datastore_search?resource_id=b80cb643-a732-480d-86b5-e03957bc82aa&limit=200').json()
```
{% endraw %}

# Data cleaning
Although the data is

Despite all the data is readily available, I had to do some data manipulation to create a long table instead of a wide table. That is, each closure period for a hawker centre should be displayed in its own row, as opposed to having all the closure periods across multiple columns for a hawker centre. The status was plotted nicely on a map using the [folium](http://python-visualization.github.io/folium/) package.

I also had to write a section of the script to monitor today's date and adjust the data needed to be represented in the map. This is particularly challenging for me as I am still not 100% comfortable working with the datetime package but that changed when I discovered the [arrow](https://arrow.readthedocs.io/en/latest/) package. The arrow package saved my life! And also, save me from all the hassle :D

Finally, I just had to deploy it on Heroku. Sounds easy, right? NOPE! Even as I followed the steps by Benedict, it still took me over 20 tries to troubleshoot. I couldn't remember what I did and it took a while to work but I still got there. As of now, the app is live [here](https://hawker-centre-db.herokuapp.com/) but it would not be available anymore on 28 November 2022 based on this [article](https://techcrunch.com/2022/08/25/heroku-announces-plans-to-eliminate-free-plans-blaming-fraud-and-abuse/).

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/202209-hawker-dashboard/202209%20hawker%20dashboard/dashboard.PNG" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

![No of daily unique posters](https://raw.githubusercontent.com/brandonyongys/brandonyongys.github.io/master/img/202209%20hawker%20dashboard/dashboard.PNG)

To give you a sense of how the dashboard looks, here's a snippet. Does it look the prettiest? Not really. Does it work as intended? Yeah.. Can it be improved? Definitely!

All in all, I am not here to show my very best work but rather to show what I have learned and what I hope to continue to learn. After all, learning is a lifelong journey. If I've already learned and could do everything as a data scientist, then how else could I improve?

=====


Src: https://getbootstrap.com/docs/4.4/layout/grid/

Sentence 1.
Sentence 2.
Sentence 3.
Sentences 1-3 would be combined into 1 single paragraph.

# A row of 3 images below
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/1.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/3.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/5.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    This is an example caption. The code above can be adjusted to show 1 image only by having 1 class only..
</div>

<div class="row justify-content-sm-center">
    <div class="col-sm-8 mt-3 mt-md-0">
        {% include figure.html path="assets/img/6.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
        {% include figure.html path="assets/img/11.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You can also have artistically styled 2/3 + 1/3 images, like these.
    Both images have rounded corners with `img-fluid rounded z-depth-1`
</div>

{% raw %}
```html
raw codes here
```
{% endraw %}