---
layout: default
title: Write-ups for Capture the Flag
---

<div id="articles">
  <h1>Articles</h1>
  <ul class="posts noList">
    {%- for post in site.posts -%}
      <li>
      	<span class="date">{{ post.date | date_to_string }}</span>
      	<h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      	<p class="description">{%- if post.description -%}{{ post.description  | strip_html | strip_newlines | truncate: 30 }}{%- else -%}{{ post.content | strip_html | strip_newlines | truncate: 30 }}{%- endif -%}</p>
      </li>
    {%- endfor -%}
  </ul>
</div>
