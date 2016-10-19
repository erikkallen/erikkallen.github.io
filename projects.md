---
title: Projects
permalink: "/projects/"
layout: page
---

{% for project in site.projects %}
{% if project.sub_page == null || project.sub_page == false  %}
![{{ project.title }}]({{project.thumbnail}}){: .project-image }
[{{ project.title }}]({{ project.url }})

  {{project.description}}

  <br style="clear:both;">
  {% endif %}
{% endfor %}
