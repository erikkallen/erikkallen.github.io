---
title: Projects
permalink: "/projects/"
layout: page
---

<div class="not-prose grid grid-cols-1 sm:grid-cols-2 gap-6">
  {% for project in site.projects %}
  {% unless project.sub_page %}
  <a href="{{ project.url | prepend: site.baseurl }}" class="group bg-white rounded-xl border border-gray-200 overflow-hidden hover:shadow-md transition-shadow" style="text-decoration:none">
    {% if project.thumbnail %}
    <div class="aspect-video bg-gray-100 overflow-hidden">
      <img src="{{ project.thumbnail }}" alt="{{ project.title }}" class="w-full h-full object-contain p-4 group-hover:scale-105 transition-transform duration-300 mix-blend-multiply">
    </div>
    {% endif %}
    <div class="p-5">
      <h2 class="text-lg font-semibold text-gray-900 group-hover:text-blue-600 transition-colors mb-1">{{ project.title }}</h2>
      {% if project.description %}
      <p class="text-sm text-gray-500 leading-relaxed">{{ project.description }}</p>
      {% endif %}
    </div>
  </a>
  {% endunless %}
  {% endfor %}
</div>
