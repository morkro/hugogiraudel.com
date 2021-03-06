---
layout: page
title: Hi there, I’m Hugo
theme: t-dark-grey
tags:
  - Hugo Giraudel
  - blog
  - css
  - sass
---

A French front-end developer working as an accessibility advocate at [N26](http://n26.com) in Berlin. Feel free to [read more about me](/about/).

{% capture last_article_index_suffix %}
  {% assign article_count = site.posts | size %}
  {% assign modulo = article_count | modulo: 10 %}
  {% if modulo == 1 %}
    st
  {% elsif modulo == 2 %}
    nd
  {% elsif modulo == 3 %}
    rd
  {% else %}
    th
  {% endif %}
{% endcapture %}

{% capture last_article_index %}
{{ site.posts | size }}{{ last_article_index_suffix | strip }}
{% endcapture %}

{% for post in site.posts limit:1 %}
{% capture last_article_title %}
{{ post.title }}
{% endcapture %}
{% capture last_article_link %}
{% if post.external %}{{ post.external.url }}{% else %}{{ post.url }}{% endif %}
{% endcapture %}
{% endfor %}

I write a lot. My {{ last_article_index | strip }} and latest article is entitled [{{ last_article_title | strip }}]({{ last_article_link }}). You can read [more articles from me](/blog/), or [search for something specific](/search/). I also had the great chance of having [wonderful people writing here](/guest/).

{% for project in site.data.projects limit:1 %}
{% capture last_project_title %}
{{ project.name }}
{% endcapture %}
{% capture last_project_link %}
{{ project.link }}
{% endcapture %}
{% endfor %}

I like to think that I am an active open-source contributor. My latest project is [{{ last_project_title | strip }}]({{ last_project_link }}). Feel free to check [more of my projects](/projects/).

{% capture current_date %}{{ site.time | date: "%s" }}{% endcapture %}

{% for event in site.data.speaking %}
{% capture event_date %}{{ event.date | date: "%s" }}{% endcapture %}
{% if event_date > current_date %}
{% capture next_event_name %}{{ event.event }}{% endcapture %}
{% capture next_event_link %}{{ event.link }}{% endcapture %}
{% capture next_event_date %}{{ event.date | date_to_long_string }}{% endcapture %}
{% endif %}
{% endfor %}

I also enjoy talking at conferences when I find time. If you would like me to attend one of your events, feel free to get in touch! You can have a look at [my past talks](/speaking/).{% if next_event_name %} Note that I will be speaking at [{{ next_event_name }}]({{ next_event_link }}), on {{ next_event_date | date: "%B %d, %Y" }}. Come say hi!{% endif %}
