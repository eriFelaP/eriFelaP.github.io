---
layout: default
permalink: /categories/
title: 分类
---

<h1>{{ page.title }}</h1>

<!-- 分类云 -->
<div class="tags_cloud">
{% assign cats = site.categories | sort %}
{% for cat in cats %}
 <span class="site-cat">
    <a href="/categories/#{{ cat | first | slugify }}"
        style="font-size: {{ cat | last | size  |  times: 4 | plus: 80  }}%">
            {{ cat[0] | replace:'-', ' ' }} ({{ cat | last | size }})
    </a>
</span>
{% endfor %}
</div>

{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    <div id="#{{ category_name | slugify }}"></div>
    <p></p>

    <h4 class="category-head">{{ category_name }}</h4>
    <a name="{{ category_name | slugify }}"></a>
      <ol class="posts">
      {% for post in site.categories[category_name] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a> &raquo; <i><span>{{ post.date | date_to_string }}</span></i></li>
      {% endfor %}
      </ol>
  </div>
{% endfor %}

