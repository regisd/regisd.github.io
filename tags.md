---
layout: default
permalink: /tags
title: Libellés
---

# Libellés

{% for tag in site.tags %}
  {% capture tag_name %}{{ tag | first }}{% endcapture %}
  {% capture tag_slug %}{{ tag_name | slugize }}{% endcapture %}
- [{{ tag_name }}](#{{tag_slug}})
{% endfor %}

<div id="archives">
{% for tag in site.tags %}
  <div class="archive-group">
    {% capture tag_name %}{{ tag | first }}{% endcapture %}
    {% capture tag_slug %}{{ tag_name | slugize }}{% endcapture %}
        
    <h2 id="{{tag_slug}}" class="tag-head">
      <i class="material-icons">label_outline</i>
      {{ tag_name }}
    </h2>
    <ul>
    {% for post in site.tags[tag_name] %}
    <article class="archive-item">
      <li><a href="{{ site.baseurl }}{{ post.url }}">{{post.title}}</a></li>
    </article>
    {% endfor %}
    </ul>
  </div>
{% endfor %}
</div>