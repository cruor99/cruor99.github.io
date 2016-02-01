---
layout: page
title: Archive
---

## Blog Posts

{% for post in site.posts %}
{% if  post.draft %}
  
{% else %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ post.url }})
{% endif %}
{% endfor %}