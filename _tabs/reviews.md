---
# the default layout is 'page'
title: Reviews
icon: fas fa-file-lines
order: 2
---

{% include lang.html %}

Notes and reviews of papers I've read, grouped by topic.

{% assign review_posts = site.categories['Reviews'] %}
{% assign sub_categories = '' | split: '' %}
{% for post in review_posts %}
  {% assign sub = post.categories[1] %}
  {% if sub %}
    {% unless sub_categories contains sub %}
      {% assign sub_categories = sub_categories | push: sub %}
    {% endunless %}
  {% endif %}
{% endfor %}
{% assign sub_categories = sub_categories | sort %}

{% for sub in sub_categories %}
{% assign posts_of_sub = review_posts | where_exp: "p", "p.categories[1] == sub" %}
<h2 class="ps-lg-2" style="margin: 2.75rem 0 0;">
  <i class="far fa-folder-open fa-fw text-muted"></i>
  {{ sub }}
  <span class="lead text-muted ps-1">{{ posts_of_sub | size }}</span>
</h2>
<ul class="content ps-0" style="margin-top: 0.5rem;">
  {% for post in posts_of_sub %}
  <li class="d-flex justify-content-between px-md-3">
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <span class="dash flex-grow-1"></span>
    {% include datetime.html date=post.date class='text-muted small text-nowrap' lang=lang %}
  </li>
  {% endfor %}
</ul>
{% endfor %}
