---
layout: page
title: Articles
banner: /assets/page-articles.jpg
tagline: "Things behind every poem"
permalink: /articles/
description: "All articles on advanced poetry techniques and the craft of writing poetry."
---
<style>
.page-content .post-header, .page-content .post-content { max-width: none; }
.article-grid { list-style: none; margin: 0; padding: 0; display: grid; gap: 16px; }
.article-grid li { position: relative; margin: 0; padding: 22px 64px 22px 26px; border: 1px solid rgba(128,128,128,.28); border-left: 3px solid #d4af6a; border-radius: 12px; background: #141831; transition: transform .2s ease, border-color .2s ease, box-shadow .2s ease; }
.article-grid li:hover { transform: translateY(-2px); border-color: #d4af6a; box-shadow: 0 10px 28px rgba(212,175,106,.12); }
.article-grid li::after { content: "\2192"; position: absolute; right: 26px; top: 50%; transform: translateY(-50%); color: #d4af6a; font-size: 1.4em; }
.article-grid .tag { display: flex; align-items: center; gap: 8px; font-size: .75em; letter-spacing: .14em; text-transform: uppercase; color: #d4af6a; }
.article-grid .tag svg { width: 16px; height: 16px; fill: none; stroke: currentColor; stroke-width: 1.8; stroke-linecap: round; stroke-linejoin: round; }
.article-grid h3 { margin: 8px 0 0; font-size: 1.15em; line-height: 1.4; }
.article-grid .post-link::after { content: ""; position: absolute; top: 0; right: 0; bottom: 0; left: 0; }
.article-grid .excerpt { margin: 8px 0 0; max-width: 62em; font-size: .92em; line-height: 1.6; opacity: .8; display: -webkit-box; -webkit-line-clamp: 2; -webkit-box-orient: vertical; overflow: hidden; }
@media (max-width: 600px) { .article-grid li { padding: 18px 44px 18px 20px; } .article-grid li::after { right: 16px; } }
@media (prefers-reduced-motion: reduce) { .article-grid li { transition: none; } .article-grid li:hover { transform: none; } }
</style>
<ul class="article-grid">
{% for post in site.posts %}
  <li>
    <span class="tag"><svg viewBox="0 0 24 24" aria-hidden="true"><path d="M3 21l3.5-1 11-11-2.5-2.5-11 11z"/><path d="M14.5 6.5L17 9"/></svg>Article</span>
    <h3><a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h3>
    <p class="excerpt">{{ post.description | default: post.excerpt | strip_html | strip | truncate: 170 }}</p>
  </li>
{% endfor %}
</ul>
