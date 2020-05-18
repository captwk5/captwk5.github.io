---
layout: page
title: Tag
permalink: /tag/
---

{% capture site_tags %}{% for tag in site.tags %}{{ tag | first }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
<!-- site_tags: {{ site_tags }} -->
{% assign tag_words = site_tags | split:',' | sort %}
<!-- tag_words: {{ tag_words }} -->

<ul class="tag-box inline">
  {% for tag in tag_words %}
    <a href="#{{ tag | cgi_escape }}" style="background-color:#eaeaea">#{{ tag }} (<span>{{ site.tags[tag] | size }}</span>)</a>
  {% endfor %}
</ul>&nbsp;&nbsp;

<div id="tags">
  {% for item in (0..site.tags.size) %}{% unless forloop.last %}
    {% capture this_word %}{{ tag_words[item] | strip_newlines }}{% endcapture %}
  <h3 id="{{ this_word | cgi_escape }}">{{ this_word }}</h3>
  <ul class="posts">
    {% for post in site.tags[this_word] %}{% if post.title != null %}
      <li itemscope>
        <span class="entry-date">
          <time datetime="{{ post.date | date_to_xmlschema }}" itemprop="datePublished">{{ post.date | date: "%B %d, %Y" }}</time>
        </span> &raquo; {% if post.category == "speaking" %}<i class="fa fa-microphone"></i> {% endif %}<a href="{{ post.url }}" style="color:blue">{{ post.title }}</a>
      </li>
    {% endif %}{% endfor %}
  </ul>
  {% endunless %}{% endfor %}
</div>

<!-- <ul class="tag-cloud">
{% for tag in site.tags %}
  <span style="font-size: {{ tag | last | size | times: 100 | divided_by: site.tags.size | plus: 70  }}%">
    <a href="#{{ tag | first | slugize }}">
      {{ tag | first }}
    </a> &nbsp;&nbsp;
  </span>
{% endfor %}
</ul>

<div id="archives">
  {% for tag in site.tags %}
    <div class="archive-group">
      {% capture tag_name %}{{ tag | first }}{% endcapture %}
      <h3 id="#{{ tag_name | slugize }}">{{ tag_name }}</h3>
      <a name="{{ tag_name | slugize }}"></a>
      {% for post in site.tags[tag_name] %}
        <article class="archive-item">
          <h5><a href="{{ root_url }}{{ post.url }}">{{post.title}}</a></h5>
        </article>
      {% endfor %}
    </div>
  {% endfor %}
</div> -->