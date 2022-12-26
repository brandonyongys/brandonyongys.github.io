---
layout: post
title: Hawker centre dashboard
tags: [dashboard, heroku, app]
comments: true
published: true

date:   2022-09-11
description: First attempt at deploying a dashboard
categories: deployment
---


I happened to stumble upon a medium post about deploying an app to analyse dengue cases in Singapore [post](https://towardsdatascience.com/creating-a-web-application-to-analyse-dengue-cases-1be4a708a533) by Benedict Soh back in late 2020's. It would have been of great use to the Singapore public to be more up-to-date with the latest news about dengue. However, the app was a static app and it did not function properly after 2 Aug 2020.

It was really cool for me to learn of a local application and it is more understandable to a layman like me. Mind you, I do not have proper technical skill and knowledge in programming and what not! I am still learning new things on the go.

Nonetheless, it did inspire me to develop an app as well but I had difficulty finding out what to do. So I pretty much procrastinated on it again until early June 2022. My team's external advisor in SGH wanted to conduct an experience and told us to spend 2 half-days per week learning new things. Considering the encouragement I received then, I finally decided to pick up the small project and try to develop and deploy a simple app.

I was digging through [data.gov.sg](https://data.gov.sg/) and found a [dataset](https://data.gov.sg/dataset/dates-of-hawker-centres-closure) about dates of hawker centre closures. Seeing that there is a temporal and spatial elements, I decided to pick it up and develop a dashboard for it. The dashboard has x main purposes:
1) Show a map of all hawker centres as points. Each point is colour coded based on its status (open, closing soon or closed).
2) Two separate tables to show a list of hawker centres that are currently closed and the upcoming closures.

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