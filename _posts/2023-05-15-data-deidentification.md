---
date: 2023-05-15

layout: post
title: How well perceived is Marina Bay Sands?
description: Sentiment analysis of MBS reviews

comments: true
published: true

---
Data is an important aspect in any data science work. Without data, tasks like modelling and feature extraction could not be done. But it need not be de-identified as the identifiers often serve little to no purpose in a data science project except at the initial stage where multiple datasets are stitched together to form a more holistic picture. 

However, as an individual, I would love to have my data de-identified as much as possible so as to protect my own privacy and confidential information such as personal health information (PHI). Such data would definitely need to be de-identified as it could expose extremely sensitive information such as HIV and AIDS status. Other than that, stolen identifiable data could be used for malicious intent. Hence, there are rules and regulations across countries to ensure PHI is fully de-identified before any work could be done including research work. In Singapore, all personal data is protected by the PDPA law, which serves as the base law, and all health records are subjected to HBRA on top of PDPA. 

De-identification is not mainly applied in the healthcare sector. It is also applied in other sectors such as financial institutions or e-commerce where the analysts could access personal information and cause clients financial losses if it is not managed well.

List of identifiers
https://www.immuta.com/blog/what-is-data-de-identification/#:~:text=There%20are%20two%20primary%20de%2Didentification%20methods%3A%20generalizing%20and%20randomizing.

Below is the list of identifiers that would need to be de-identified based on the link above:
Names
Dates, except the year
Telephone numbers
Geographic data
Fax numbers
Social Security numbers
Email addresses
Medical record numbers
Account numbers
Health plan beneficiary numbers
Certificate/license numbers
Vehicle identifiers and serial numbers, including license plates
Web URLs
Device identifiers and serial numbers
Internet protocol addresses
Full face photos and comparable images
Biometric identifiers
Any unique identifying number, characteristic, or code

De-identification techniques
1) pseudonymization 
- individuals are given another set of identifiers (e.g. Brandon is renamed to Michael, all dates are shifted by n days). This helps the user to track the individuals across time. However, this step alone does not prevent the user from re-identifying the individual if there are specific unique set of characteristics. 

2) k-anonymization
- this is when data is dealt in such a way that any subset of data would contain at least k individuals sharing the same characteristics. E.g. there may be many individuals below the age 80 with positive HIV and not many individuals aged 80 and above with positive HIV. Instead, the age threshold may be lowered 80-> 40 so that there are more individuals in the 40+HIV subset. This makes re-identification effort by chance significantly less likely. 


Sample codes to de-identify

Conclusion




<hr>


reference: 
https://github.com/AxelBogos/AxelBogos.github.io

_xx_ 			- italic
**xx** 			- bold
# xxx			- header
[display text](link)	- hyper link 
[display text][ref] 	[ref]: website
![display text](link) 		- images
> text 				- block quote
* text 				- unordered list
    * text 			- unordered sublist
1. text 			- ordered list


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

For plotly figure, use below
<iframe width="1000" height="750" frameborder="0" scrolling="yes" src="/assets/img/mbs_reviews/avg_rating_over_time.html"></iframe>



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
