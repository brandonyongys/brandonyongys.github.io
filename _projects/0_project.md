---
layout: page
title: project 1 # Project post title
description: a project with a background image # Project post description
img: assets/img/12.jpg # Not necessary to have this image, will be used as thumbnail
redirect: https://unsplash.com # Insert link if want to redirect to another website, else ignore/remove this.
importance: 1
category: serious # serious / fun, if wrong category, the post won't be posted

comments: true
published: false
---

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