---
title: "Blog Posts"
layout: single
permalink: /blogs/
author_profile: true
---

<style>
  /* 强制让博客列表的中文字体更现代 (苹方/微软雅黑) */
  .archive__item-title, .post-list a {
    font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif;
  }
</style>
{% assign categories = site.categories | sort %}

{% for category in categories %}
  {% assign category_name = category[0] %}
  {% assign posts_in_category = category[1] %}

  <div class="category-section" style="margin-bottom: 40px;">
    <h2 class="archive__item-title" style="border-bottom: 2px solid #f2f3f3; padding-bottom: 10px; margin-top: 30px;">
      📂 {{ category_name }}
    </h2>

    <ul class="post-list" style="list-style: none; padding-left: 0;">
      {% for post in posts_in_category %}
        <li style="margin-bottom: 15px;">
          <a href=" " style="font-weight: bold; font-size: 1.1em; text-decoration: none; color: #333;">
            {{ post.title }}
          </a >
          
          <div style="font-size: 0.85em; color: #888; margin-top: 2px;">
            <i class="far fa-calendar-alt"></i> {{ post.date | date: "%Y-%m-%d" }}
            
            {% if post.tags.size > 0 %}
              <span style="margin-left: 10px;">
                <i class="fas fa-tags"></i> 
                {{ post.tags | join: ", " }}
              </span>
            {% endif %}
          </div>
          
          {% if post.excerpt %}
            <p style="margin-top: 5px; font-size: 0.9em; color: #555;">
              {{ post.excerpt | strip_html | truncate: 120 }}
            </p >
          {% endif %}
        </li>
      {% endfor %}
    </ul>
  </div>

{% endfor %}

{% if site.categories.size == 0 %}
  <p>No posts found.</p >
{% endif %}