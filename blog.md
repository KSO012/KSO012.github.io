---
layout: default
title: Blog
nav: blog
permalink: /blog/
---
<section class="page-intro"><div class="eyebrow">NOTES & WRITING</div><h1>Blog</h1><p>개발하며 배운 것과 생각을 기록합니다.</p></section>
<div class="post-list">
{% for post in site.posts %}
  <a class="post-row" href="{{ post.url | relative_url }}"><span class="post-date">{{ post.date | date: '%Y. %m. %d' }}</span><span class="post-title">{{ post.title }}</span><span aria-hidden="true">↗</span></a>
{% else %}
  <p>아직 작성한 글이 없습니다. <code>_posts</code> 폴더에 Markdown 파일을 추가하면 여기에 표시됩니다.</p>
{% endfor %}
</div>
