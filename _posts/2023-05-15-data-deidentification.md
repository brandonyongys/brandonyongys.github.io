---
date: 2023-05-15

layout: post
title: How well perceived is Marina Bay Sands?
description: Sentiment analysis of MBS reviews

comments: true
published: true

# ORIGINAL 
# Data is an important aspect in any data science work. Without data, tasks like modelling and feature extraction could not be done. But it need not be de-identified as the identifiers often serve little to no purpose in a data science project except at the initial stage where multiple datasets are stitched together to form a more holistic picture. 

# However, as an individual, I would love to have my data de-identified as much as possible so as to protect my own privacy and confidential information such as personal health information (PHI). Such data would definitely need to be de-identified as it could expose extremely sensitive information such as HIV and AIDS status. Other than that, stolen identifiable data could be used for malicious intent. Hence, there are rules and regulations across countries to ensure PHI is fully de-identified before any work could be done including research work. In Singapore, all personal data is protected by the PDPA law, which serves as the base law, and all health records are subjected to HBRA on top of PDPA. 

# De-identification is not mainly applied in the healthcare sector. It is also applied in other sectors such as financial institutions or e-commerce where the analysts could access personal information and cause financial losses to either the clients or company, or worse both, if it is not managed well.

---

Data is a critical component in any data science project, as it serves as the foundation for tasks such as modeling and feature extraction. However, in some cases, it is essential to de-identify data to protect the privacy of individuals and sensitive information, such as personal health information (PHI). In such instances, identifying information such as names and addresses may serve little to no purpose, except during the initial stage where multiple datasets are combined to form a more comprehensive picture.

In Singapore, the Personal Data Protection Act (PDPA) serves as the base law protecting personal data, while the Healthcare Services Act's (HSA) provisions safeguard the confidentiality of medical records. Such regulations are necessary to ensure that PHI is adequately de-identified before any research work or data analysis is performed. This is particularly crucial in the healthcare sector, where identifying data could expose sensitive information such as HIV and AIDS status, leading to stigmatization and discrimination.

However, de-identification is not only applicable in the healthcare industry but also other sectors such as finance and e-commerce. Analysts who access personal information without proper management could cause significant financial losses to clients and the company. As such, it is crucial to adhere to regulatory requirements and best practices when handling sensitive data.

In summary, de-identification is an essential practice for protecting personal information and sensitive data in various industries, including healthcare, finance, and e-commerce. Regulatory frameworks such as the PDPA and HSA provide guidelines and rules that companies and individuals must follow when dealing with personal information to ensure compliance and mitigate risks.


# Personally Identifiable Information (PII)
According to ChatGPT, below are some of the common PII that are typically de-identified, which overlaps with the list found [here](https://www.immuta.com/blog/what-is-data-de-identification/#:~:text=There%20are%20two%20primary%20de%2Didentification%20methods%3A%20generalizing%20and%20randomizing). The list is not exhaustive and it may vary depending on the context, sensitivity of the data as well as the regulatory requirements.
<ul>
    <li>Names (including first, middle, and last names)</li>
    <li>Addresses (including street address, city, state/province, and postal code)</li>
    <li>Phone numbers (including mobile, home, and work numbers)</li>
    <li>Email addresses</li>
    <li>Social Security Numbers (or equivalent national identification numbers)</li>
    <li>Driver's license numbers</li>
    <li>Passport numbers</li>
    <li>Health insurance policy numbers</li>
    <li>Medical record numbers</li>
    <li>Biometric identifiers (such as fingerprints or facial recognition data)</li>
</ul>

None of these common identifiers came as a surprise as having any one of these would directly identify the individuals. There are other identifiers such as race and age which could identify the individual. However, such identifiers would need to exist in a particular set in order to identify the individual with high confidence.



# De-identification techniques

De-identification can be achieved through pseudonymization, which involves replacing the individual's set of identifiers with another set of identifiers that may or may not be random or nonsensical. For instance, a name like `Brandon` could be replaced with `Michael` or even a random alphanumeric string such as `jkas89sdfln298dxciu`. However, pseudonymization may not be appropriate for other identifiers, such as dates, that are required to study the temporal or spatial effects. Furthermore, pseudonymization alone may not be sufficient to protect against re-identification if there are specific unique characteristics that can be linked back to the individual.

To provide further privacy protection, the k-anonymization technique can be employed. This method ensures that any subset of individuals sharing a set of specific unique characteristics includes at least k individuals. For example, if there are very few individuals aged 95 and above, they could be grouped together with a subgroup of individuals aged 80 to 94 years old to protect their identities. Any analysis conducted on this group would not reveal the identity of any specific individual.



# Sample de-identification codes

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
