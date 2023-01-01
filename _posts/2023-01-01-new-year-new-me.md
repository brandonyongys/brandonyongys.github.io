---
date: 2023-01-01

layout: post
title: New year, new me
description: Listing out the goals for my github page for 2023
tags: [happy new year]
categories: app

comments: true
published: false

---
New year, new me eh. I have been rather slack in my own professional development for the past 1 year (not only that actually). Now I have to focus on my professional and personal goals and aim to achieve at least 80% of them by end of the year! No more procrastinating!

Professional (Target: 4/5):
1. Monthly post on github page by the last day of the month (12 posts in total)
1. Complete the friends' analysis by end of January
1. Develop an image generator for xxx.
1. Develop a medical image generator.
1. Deploy a dashboard using one of the dataset in Data.gov.sg using API and AWS. 

Career (Target: 3/4):
1. Deploy the Prophet model for the hospital within the timeline (May 2023)
1. Develop a model that takes in irregular inputs for prediction.
1. Develop a medical image generator.
1. Find an employer that better recognizes the work I've done so far.

Personal (Target 3/4):
1. Travel to Turkey (booked a tour in February).
1. Travel to UK (aim to travel in early November).
1. Lose body fats (body fats percentage from 20% to 15%, 77kg -> 73kg minimally).
1. Be healthier by eating more fruits, veggies and meat for 80% of the meals while reducing carbs intake to lose body fats (aim to drop to 68 kg)


Next post below:

simple clone the git as own repo. 
rename as brandonyongys.github.io when cloning.
change the url to brandonyongys.github.io in config file
allow all actions
check that the pages are deploy from branch (gh-pages) 
save then wait
open own github.io


You can write regular [markdown](http://markdowntutorial.com/) here and Jekyll will automatically convert it to a nice webpage.  I strongly encourage you to [take 5 minutes to learn how to write in markdown](http://markdowntutorial.com/) - it'll teach you how to transform regular text into bold/italics/headings/tables/etc.

**Here is some bold text**

Create horizantal line:
<hr>

## Here is a secondary heading

# Create list
<ul>
    <li>brunch</li>
    <li>fixie</li>
    <li>raybans</li>
    <li>messenger bag</li>
</ul>

# to quote someone:
For a single line even if the blockquote has multiple lines:
<blockquote>
    We do not grow absolutely, chronologically. We grow sometimes in one dimension, and not in another, unevenly. We grow partially. We are relative. We are mature in one realm, childish in another.
    —Anais Nin
</blockquote>

OR 
for multiple quote lines
> We do not grow absolutely, chronologically. We grow sometimes in one dimension, and not in another, unevenly. We grow partially. We are relative. We are mature in one realm, childish in another.
> —Anais Nin

# Here's a useless table:

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |


# Create image

![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/9.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/7.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A simple, elegant caption looks good between image rows, after each row, or doesn't have to be there at all.
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/8.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/10.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Zoomable images with zoomable=true.
</div>

# Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.
