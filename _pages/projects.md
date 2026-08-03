---
layout: default
title: Diya Mehta - Portfolio
permalink: /projects/
---

<div class="gallery-container">
<div class="project-gallery">
    {% for project in site.projects %}
      <div class="gallery-card">
        <a href="{{ project.url | relative_url }}">
          <img src="{{ project.image | relative_url }}" alt="{{ project.title }}">
          <div class="gallery-card-content">
            <h3>{{ project.title }}</h3>
            <p>{{ project.description }}</p>
          </div>
        </a>
      </div>
    {% endfor %}
</div>
</div>