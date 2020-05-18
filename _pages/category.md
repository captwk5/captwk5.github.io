---
layout: page
title: Category
permalink: /category/
---

<a href="https://captwk5.github.io/">BLOG1</a>

<div class="container">
  <a href="https://captwk5.github.io/">BLOG2</a>
  <div class="post-info">
    {% if page.tags.size >= 1 %}
    <span class="post-tags">
      posted in
      {% for tag in page.tags %}
        <a href="{{ site.baseurl }}/tag/{{ tag }}" class="post-tags__tag">{{ tag }}</a>
      {% endfor %}
    </span>
    {% endif %}
    <span class="post__meta">
      <span class="post__date"> on <a href="{{post.url | prepend: site.baseurl}}">
        <time datetime="{{ page.date | date_to_xmlschema }}">{{page.date | date: '%b %d, %Y'}}</time></a>
      </span>
      <span class="article__author"> by <a href="{{site.baseurl}}/about/">{{ site.author.name }}</a></span>
    </span>
  </div>
</div>