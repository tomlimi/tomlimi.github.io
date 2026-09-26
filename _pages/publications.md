---
layout: archive
title: "Publications"
permalink: /publications/
author_profile: true
---

{% if author.googlescholar %}
  You can also find my articles on <u><a href="{{author.googlescholar}}">my Google Scholar profile</a>.</u>
{% endif %}

{% include base_path %}

{% assign publications_by_date = site.publications | sort: 'date' | reverse %}
{% capture myte_listing %}
  {% for post in site.publications %}
    {% if post.permalink == 'publication/myte-2024-acl' %}
      {% include archive-single.html %}
    {% endif %}
  {% endfor %}
{% endcapture %}

{% for post in publications_by_date %}
  {% unless post.selected == false %}
    {% if post.featured %}
      {% include archive-single.html %}
    {% endif %}
  {% endunless %}
{% endfor %}

{% for post in publications_by_date %}
  {% unless post.selected == false %}
    {% unless post.featured %}
      {% comment %}Place MYTE immediately above MAGNET while keeping their actual publication dates.{% endcomment %}
      {% if post.permalink == '/publication/magnet-2024-neurips' %}{{ myte_listing }}{% endif %}
      {% unless post.permalink == 'publication/myte-2024-acl' %}
        {% include archive-single.html %}
      {% endunless %}
    {% endunless %}
  {% endunless %}
{% endfor %}
