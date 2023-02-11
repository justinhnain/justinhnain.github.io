---
layout: archive
title: "Portfolio"
permalink: /portfolio/
author_profile: true
classes: wide
---

{% include base_path %}

<div class="grid__wrapper">
  {% for post in site.portfolio %}
    {% include archive-single.html type="grid" %}
  {% endfor %}
</div>

<!-- ---
title: "Portfolio"
layout: collection
permalink: /portfolio/
collection: portfolio
entries_layout: grid
classes: wide
--- -->
