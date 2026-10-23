---
layout: default
description: "Learn advanced poetry techniques with simple explanations and examples from my own poems. Read the articles and apply them in your poetry."
---
<style>
.hero { padding: 48px 0 32px; }
.hero h1 { font-size: 2.3em; line-height: 1.2; margin-bottom: 16px; }
.hero p { font-size: 1.1em; max-width: 34em; opacity: 0.9; }
.btn { display: inline-block; margin-top: 12px; padding: 12px 28px; border-radius: 999px; background: #d4af6a; color: #0f1220 !important; font-weight: 600; text-decoration: none !important; }
.btn:hover { background: #e6c685; }
.landing-section h2 { margin: 48px 0 16px; font-size: 1.5em; }
.cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(210px, 1fr)); gap: 16px; }
.card { border: 1px solid rgba(128, 128, 128, 0.35); border-radius: 12px; padding: 20px; }
.card h3 { font-size: 1.1em; margin-bottom: 8px; }
.card p { margin: 0; font-size: 0.95em; opacity: 0.85; }
.closing { margin: 56px 0 24px; padding: 32px 24px; border: 1px solid rgba(128, 128, 128, 0.35); border-radius: 12px; text-align: center; }
.closing h2 { margin-top: 0; font-size: 1.5em; }
</style>

<div class="hero">
  <h1>Learn advanced poetry techniques and use them in your own poems</h1>
  <p>Express your feelings in poetry in more than one way. Every technique is explained in simple words, with examples from my own poems.</p>
  <a class="btn" href="{{ '/articles/' | relative_url }}">Read the articles</a>
</div>

<div class="landing-section">
  <h2>What you will find here</h2>
  <div class="cards">
    <div class="card"><h3>Advanced techniques</h3><p>Perception-based methods such as negative capability, the objective correlative and defamiliarization.</p></div>
    <div class="card"><h3>Simple explanations</h3><p>Each method in plain words, so you can understand it and try it the same day.</p></div>
    <div class="card"><h3>Examples from my poems</h3><p>See every technique at work in lines from my own poetry.</p></div>
  </div>
</div>

<div class="landing-section">
  <h2>Latest articles</h2>
  <ul class="post-list">
  {% for post in site.posts limit:3 %}
    <li>
      <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
      <h3><a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h3>
    </li>
  {% endfor %}
  </ul>
  <p><a href="{{ '/articles/' | relative_url }}">See all articles &rarr;</a></p>
</div>

<div class="closing">
  <h2>Ready to try a new technique?</h2>
  <p>Read the articles and find techniques to apply in your poetry right now!</p>
  <a class="btn" href="{{ '/articles/' | relative_url }}">Start reading</a>
</div>
