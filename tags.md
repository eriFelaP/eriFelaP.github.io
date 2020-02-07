---
layout: default
permalink: /tags/
title: 标签
---

<h1>{{ page.title }}</h1>

<!-- 标签云 -->
<div class="tags_cloud">
{% assign tags = site.tags | sort %}
{% for tag in tags %}
 <span class="site-tag">
    <a href="/tags/#{{ tag | first | slugify }}"
        style="font-size: {{ tag | last | size  |  times: 4 | plus: 80  }}%">
            {{ tag[0] | replace:'-', ' ' }} ({{ tag | last | size }})
    </a>
</span>
{% endfor %}
</div>

{% for tag in site.tags %}
  <div class="archive-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    <div id="{{ tag_name | slugify }}"></div>
    <p></p>
    <h4 class="tag-head">{{ tag_name }}</h4>
    <a name="{{ tag_name | slugify }}"></a>
      <ol class="posts">
      {% for post in site.tags[tag_name] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a> &raquo; <i><span>{{ post.date | date_to_string }}</span></i></li>
      {% endfor %}
      </ol>
  </div>
{% endfor %}

