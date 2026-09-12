---
layout: page
title: projects
permalink: /projects/
# description: A growing collection of your cool projects.
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

{% comment %}
PROJECT STARTER TEMPLATE
Copy this into a new file under _projects/ and replace the placeholder values.
The project card uses title, description, img, importance, and category.

---
layout: page
title: "Project title"
description: "One sentence describing the project."
img: assets/img/project-cover.jpg
importance: 1
category: work
github: https://github.com/username/repository
---

Describe the problem, your contribution, the technical approach, and the result.

IMAGE GALLERY
Use the gallery and figure examples from _projects/1_project.md.

PROJECT WITHOUT AN IMAGE
Set `img:` to an empty value and keep the rest of the front matter.

EXTERNAL PROJECT
Add `redirect: https://example.com/project` to send the project card directly
to another site. Use this instead of `github` when the project has no detail page.

PROJECT WITH COMMENTS
Add `giscus_comments: true` after configuring Giscus in _config.yml.

PROJECT WITH PUBLICATIONS
Add `related_publications: true` when the project should show linked bibliography
entries. Keep the matching publication keys in _bibliography/ and _data/.
{% endcomment %}

<!-- pages/projects.md -->
<div class="projects">
{% if site.enable_project_categories and page.display_categories %}
  <!-- Display categorized projects -->
  {% for category in page.display_categories %}
  <a id="{{ category }}" href=".#{{ category }}">
    <h2 class="category">{{ category }}</h2>
  </a>
  {% assign categorized_projects = site.projects | where: "category", category %}
  {% assign sorted_projects = categorized_projects | sort: "importance" %}
  <!-- Generate cards for each project -->
  {% if page.horizontal %}
  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate cards for each project -->

{% if page.horizontal %}

  <div class="container">
    <div class="row row-cols-1 row-cols-md-2">
    {% for project in sorted_projects %}
      {% include projects_horizontal.liquid %}
    {% endfor %}
    </div>
  </div>
  {% else %}
  <div class="row row-cols-1 row-cols-md-3">
    {% for project in sorted_projects %}
      {% include projects.liquid %}
    {% endfor %}
  </div>
  {% endif %}
{% endif %}
</div>
