---
layout: default
title: Projects
---

<div id="projects">
  <h1>Projects</h1>
  <ul class="posts noList">
    {%- for project in site.projects -%}
      <li>
        <span class="date">{{ project.date | date_to_string }}</span>
        <h3><a href="{{ project.url | relative_url }}">{{ project.title }}</a></h3>
        <p class="description">{%- if project.description -%}{{ project.description | strip_html | strip_newlines | truncate: 30 }}{%- else -%}{{ project.content | strip_html | strip_newlines | truncate: 30 }}{%- endif -%}</p>
      </li>
    {%- endfor -%}
  </ul>
</div>
