---
layout: page
title: Blog posts
linktitle: Archive
permalink: /en/archive/
---

{% for post in site.posts %}
  * {{ post.date | date_to_string }} &raquo; [ {{ post.title }} ]({{ site.baseurl }}{{ post.url }})
{% endfor %}
