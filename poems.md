---
layout: page
title: Poems
permalink: /poems/
description: "Original poems by Skyler."
---
<style>
.poem-list { list-style: none; margin: 0; padding: 0; }
.poem-list li { display: flex; align-items: center; gap: 20px; margin-bottom: 28px; }
.poem-thumb { flex: 0 0 auto; }
.poem-thumb img { display: block; width: 120px; height: 120px; object-fit: cover; object-position: 70% 50%; border-radius: 8px; }
.poem-list h3 { margin: 0; }
@media (max-width: 600px) { .poem-list li { gap: 16px; } .poem-thumb img { width: 88px; height: 88px; } }
</style>

{% assign all_poems = site.poems | sort: "date" | reverse %}
<ul class="poem-list">
{% for poem in all_poems %}
  <li>
    <a class="poem-thumb" href="{{ poem.url | relative_url }}">
      <img src="{{ poem.image | relative_url }}" alt="{{ poem.image_alt | escape }}" width="120" height="120" loading="lazy">
    </a>
    <h3><a class="post-link" href="{{ poem.url | relative_url }}">{{ poem.title | escape }}</a></h3>
  </li>
{% endfor %}
</ul>
