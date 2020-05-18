---
layout: page
title: Category
permalink: /category/
---

<a href="https://captwk5.github.io/">BLOG</a>

{% if page.tags.size >= 1 %}
  <span class="post-tags">
    {% for tag in page.tags %}
      <a href="{{ site.baseurl }}/tag/{{ tag }}" class="post-tags__tag">{{ tag }}</a>
    {% endfor %}
  </span>
{% endif %}