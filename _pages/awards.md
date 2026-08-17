---
layout: page
permalink: /awards/
title: "Awards & Service"
description: Honors and professional service.
nav: true
nav_order: 3
---

## Honors and awards

{% assign awards = site.data.cv.cv.sections.Awards %}

<ul>
  {% for award in awards %}
    <li>
      <strong>{{ award.title }}</strong> — {{ award.awarder }}, <em>{{ award.date }}</em><br>
      <em>{{ award.summary }}</em>
    </li>
  {% endfor %}
</ul>

---

## Professional service

### Reviewer

{% assign services = site.data.cv.cv.sections['Professional Service'] %}

<ul>
  {% for service in services %}
    <li>{{ service.bullet }}</li>
  {% endfor %}
</ul>
