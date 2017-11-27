---
layout: default
permalink: /categories
title: Catégories
---

# Catégories

{% for category in site.categories %}
  {% capture category_name %}{{ category | first }}{% endcapture %}
  {% capture category_slug %}{{ category_name | slugize }}{% endcapture %}
- [{{ category_name }}](#{{category_slug}})
{% endfor %}

<div id="archives">
{% for category in site.categories %}
  <div class="archive-group">
    {% capture category_name %}{{ category | first }}{% endcapture %}
    {% capture category_slug %}{{ category_name | slugize }}{% endcapture %}
        
    <h2 id="{{category_slug}}" class="category-head">
      <i class="material-icons">folder</i>
      {{ category_name }}
    </h2>
    <ul>
    {% for post in site.categories[category_name] %}
    <article class="archive-item">
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></li>
    </article>
    {% endfor %}
    </ul>
  </div>
{% endfor %}
</div>