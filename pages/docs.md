---
layout: page
title: Technical Documentation
permalink: /docs/
---

# Technical Documentation

Welcome to my **{{ site.title }}** document library! Here you can quickly jump to a particular page.

<div class="section-index">
    <hr class="panel-line">
    {% for post in site.docs  %}        
    <div class="entry">
    <h5><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h5>
    <p>{{ post.description }}</p>
    </div>{% endfor %}
</div>

 
>If you're looking for more creative writing samples, go to the [Other Writing Samples](news.md) page.  I'm currently curating different types of articles ranging from:
>- CMC Arthtris (Thumb Arthritis)
>- Herbs: Benefits and Remedies
>- Unaweep Tabeguache Scenic Byway
>- What can I do with Comfrey Leaf?
>- The difference between writing Group Policy features and API features
>
>...and more to come this year!  Keep checking back.