---
layout: page
title: Poems
banner: /assets/page-poems.jpg
tagline: "Original poems with raw emotion."
permalink: /poems/
description: "Original poems by Skyler that put raw emotion through perspective, from romance and dark themes to moments of happiness."
---
<style>
.page-content .post-header, .page-content .post-content { max-width: none; }
.poem-grid { list-style: none; margin: 0; padding: 0; display: grid; grid-template-columns: repeat(3, 1fr); gap: 18px; }
.poem-grid li { position: relative; margin: 0; padding: 40px 24px 26px; text-align: center; border: 1px solid rgba(212,175,106,.3); border-radius: 90px 90px 14px 14px; background: radial-gradient(ellipse at 50% 0%, rgba(212,175,106,.16), rgba(212,175,106,0) 70%), #121629; transition: transform .2s ease, border-color .2s ease, box-shadow .2s ease; }
.poem-grid li:hover { transform: translateY(-3px); border-color: #d4af6a; box-shadow: 0 10px 28px rgba(212,175,106,.12); }
.poem-grid .tag { display: flex; align-items: center; justify-content: center; gap: 8px; font-size: .75em; letter-spacing: .14em; text-transform: uppercase; color: #d4af6a; }
.poem-grid .tag svg { width: 16px; height: 16px; }
.poem-grid h3 { margin: 8px 0 0; font-size: 1.15em; line-height: 1.4; }
.poem-grid .post-link::after { content: ""; position: absolute; top: 0; right: 0; bottom: 0; left: 0; }
.poem-grid .excerpt { margin: 10px 0 0; font-size: .92em; line-height: 1.6; opacity: .8; }
@media (max-width: 899px) { .poem-grid { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 600px) { .poem-grid { grid-template-columns: 1fr; gap: 14px; } }
@media (prefers-reduced-motion: reduce) { .poem-grid li { transition: none; } .poem-grid li:hover { transform: none; } }
</style>
{% capture butterfly %}<svg viewBox="0 0 24 24" aria-hidden="true"><g fill="currentColor" stroke="none"><path d="M11 11C9.5 7 5.5 4 1.5 4.5 1.5 8 3 12 8 13.5 9.5 13.5 10.5 12.5 11 11z"/><path d="M11 13.5C8.5 14.5 5.8 16 6.5 19.5 9 19.5 11 17.5 11 13.5z" opacity=".5"/><g transform="translate(24 0) scale(-1 1)"><path d="M11 11C9.5 7 5.5 4 1.5 4.5 1.5 8 3 12 8 13.5 9.5 13.5 10.5 12.5 11 11z"/><path d="M11 13.5C8.5 14.5 5.8 16 6.5 19.5 9 19.5 11 17.5 11 13.5z" opacity=".5"/></g></g></svg>{% endcapture %}
{% assign all_poems = site.poems | sort: "date" | reverse %}
<ul class="poem-grid">
{% for poem in all_poems %}
  <li>
    <span class="tag">{{ butterfly }}Poem</span>
    <h3><a class="post-link" href="{{ poem.url | relative_url }}">{{ poem.title | escape }}</a></h3>
    <p class="excerpt">{{ poem.description | strip_html | strip | truncate: 130 }}</p>
  </li>
{% endfor %}
</ul>
