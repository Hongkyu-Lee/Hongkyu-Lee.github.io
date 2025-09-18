---
layout: page
title: projects
permalink: /projects/
description: A growing collection of your cool projects.
nav: true
nav_order: 3
display_categories: [work, fun]
horizontal: false
---

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
  <!-- Generate list layout for each project -->
  <ul class="post-list">
    {% for project in sorted_projects %}
      <li>
        <div class="row">
          {% if project.img %}
            <div class="col-sm-3">
              <a href="{% if project.redirect %}{{ project.redirect }}{% else %}{{ project.url | relative_url }}{% endif %}">
                {% include figure.liquid loading="eager" path=project.img sizes="200px" alt="project thumbnail" class="img-fluid" %}
              </a>
            </div>
            <div class="col-sm-9">
          {% else %}
            <div class="col-sm-12">
          {% endif %}
            <h3>
              <a class="post-title" href="{% if project.redirect %}{{ project.redirect }}{% else %}{{ project.url | relative_url }}{% endif %}">{{ project.title }}</a>
            </h3>
            <p>{{ project.description }}</p>
            {% if project.github %}
              <p class="post-meta">
                <a href="{{ project.github }}"><i class="fa-brands fa-github fa-sm"></i> View on GitHub</a>
                {% if project.github_stars %}
                  <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                    <i class="fa-solid fa-star"></i>
                    <span id="{{ project.github_stars }}-stars"></span>
                  </span>
                {% endif %}
              </p>
            {% endif %}
            </div>
        </div>
      </li>
    {% endfor %}
  </ul>
  {% endfor %}

{% else %}

<!-- Display projects without categories -->

{% assign sorted_projects = site.projects | sort: "importance" %}

  <!-- Generate list layout for each project -->

  <!-- List layout for projects -->
  <ul class="post-list">
    {% for project in sorted_projects %}
      <li>
        <div class="row">
          {% if project.img %}
            <div class="col-sm-3">
              <a href="{% if project.redirect %}{{ project.redirect }}{% else %}{{ project.url | relative_url }}{% endif %}">
                {% include figure.liquid loading="eager" path=project.img sizes="200px" alt="project thumbnail" class="img-fluid" %}
              </a>
            </div>
            <div class="col-sm-9">
          {% else %}
            <div class="col-sm-12">
          {% endif %}
            <h3>
              <a class="post-title" href="{% if project.redirect %}{{ project.redirect }}{% else %}{{ project.url | relative_url }}{% endif %}">{{ project.title }}</a>
            </h3>
            <p>{{ project.description }}</p>
            {% if project.github %}
              <p class="post-meta">
                <a href="{{ project.github }}"><i class="fa-brands fa-github fa-sm"></i> View on GitHub</a>
                {% if project.github_stars %}
                  <span class="stars" data-toggle="tooltip" title="GitHub Stars">
                    <i class="fa-solid fa-star"></i>
                    <span id="{{ project.github_stars }}-stars"></span>
                  </span>
                {% endif %}
              </p>
            {% endif %}
            </div>
        </div>
      </li>
    {% endfor %}
  </ul>
{% endif %}
</div>
