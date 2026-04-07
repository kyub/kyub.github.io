---
layout: default
title: Home
---

<div class="home-archive">
  <h1 class="site-heading">{{ site.title }}</h1>
  <p class="site-subheading">{{ site.description }}</p>

  <hr class="section-divider">

  <div class="archive-sections">

    <div class="archive-section">
      <h2><a href="{{ '/papers/' | relative_url }}">Papers</a></h2>
      <p class="section-desc">논문 리뷰 및 요약 정리</p>
      <ul class="post-list">
        {% assign paper_posts = site.posts | where: "section", "papers" %}
        {% for post in paper_posts limit:5 %}
          <li class="post-item">
            <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </li>
        {% endfor %}
      </ul>
      {% if paper_posts.size > 5 %}
        <a href="{{ '/papers/' | relative_url }}" class="see-all">전체 보기 →</a>
      {% endif %}
    </div>

    <div class="archive-section">
      <h2><a href="{{ '/studies/' | relative_url }}">Studies</a></h2>
      <p class="section-desc">개인 공부</p>
      <ul class="post-list">
        {% assign study_posts = site.posts | where: "section", "studies" %}
        {% for post in study_posts limit:5 %}
          <li class="post-item">
            <span class="post-date">{{ post.date | date: "%Y-%m-%d" }}</span>
            <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
          </li>
        {% endfor %}
      </ul>
      {% if study_posts.size > 5 %}
        <a href="{{ '/studies/' | relative_url }}" class="see-all">전체 보기 →</a>
      {% endif %}
    </div>

  </div>
</div>
