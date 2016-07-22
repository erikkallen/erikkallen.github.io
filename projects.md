---
layout: page
title: Projects
permalink: /projects/
---

{% for project in site.projects %}
![{{ project.title }}]({{project.thumbnail}}){: .project-image }
[{{ project.title }}]({{ project.url }})

  {{project.description}}

  <br style="clear:both;">
{% endfor %}
