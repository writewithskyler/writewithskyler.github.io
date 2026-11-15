---
layout: default
description: "Learn advanced poetry techniques with simple explanations and examples from my own poems. Read the articles and apply them in your poetry."
---
<style>
.btn { display: inline-block; margin-top: 12px; padding: 12px 28px; border-radius: 999px; background: #d4af6a; color: #0f1220 !important; font-weight: 600; text-decoration: none !important; }
.btn:hover { background: #e6c685; }
.landing-section h2 { margin: 48px 0 16px; font-size: 1.5em; }
.cards { display: grid; grid-template-columns: repeat(auto-fit, minmax(210px, 1fr)); gap: 16px; }
.card { border: 1px solid rgba(128, 128, 128, 0.35); border-radius: 12px; padding: 20px; }
.card h3 { font-size: 1.1em; margin-bottom: 8px; }
.card p { margin: 0; font-size: 0.95em; opacity: 0.85; }
.closing { margin: 56px 0 24px; padding: 32px 24px; border: 1px solid rgba(128, 128, 128, 0.35); border-radius: 12px; text-align: center; }
.closing h2 { margin-top: 0; font-size: 1.5em; }
.carousel { position: relative; margin: 24px 0 8px; border-radius: 16px; overflow: hidden; border: 1px solid rgba(212, 175, 106, 0.25); }
.carousel.is-js .carousel-track { display: flex; transition: transform 0.8s ease; }
.slide { box-sizing: border-box; display: flex; flex-direction: column; justify-content: center; min-height: 380px; padding: 56px 48px 76px; }
.carousel.is-js .slide { flex: 0 0 100%; }
.slide-articles { background: linear-gradient(90deg, rgba(15, 18, 32, 0.8) 0%, rgba(15, 18, 32, 0.6) 45%, rgba(15, 18, 32, 0) 75%), url("{{ '/assets/hero-articles.jpg' | relative_url }}") right center / cover no-repeat #0f1220; }
.slide-poems { background: linear-gradient(90deg, rgba(15, 18, 32, 0.8) 0%, rgba(15, 18, 32, 0.6) 45%, rgba(15, 18, 32, 0) 75%), url("{{ '/assets/hero-poems.jpg' | relative_url }}") right center / cover no-repeat #0f1220; }
.slide h1, .slide h2 { margin: 0 0 16px; max-width: 17em; font-size: 2.1em; line-height: 1.2; }
.slide p { margin: 0 0 8px; max-width: 30em; font-size: 1.1em; opacity: 0.9; }
.slide .btn { align-self: flex-start; }
.carousel-controls { position: absolute; left: 0; right: 0; bottom: 16px; display: flex; justify-content: center; align-items: center; gap: 6px; }
.carousel-controls button { cursor: pointer; }
.carousel-controls .arrow { width: 36px; height: 36px; border: 1px solid rgba(212, 175, 106, 0.5); border-radius: 50%; background: rgba(15, 18, 32, 0.7); color: #d4af6a; font-size: 18px; line-height: 1; }
.carousel-controls .dot { position: relative; width: 24px; height: 24px; padding: 0; border: 0; background: none; }
.carousel-controls .dot::before { content: ""; position: absolute; inset: 7px; border: 1px solid #d4af6a; border-radius: 50%; }
.carousel-controls .dot[aria-current="true"]::before { background: #d4af6a; }
@media (max-width: 600px) {
  .slide { min-height: 430px; padding: 40px 22px 76px; }
  .slide h1, .slide h2 { font-size: 1.6em; }
  .slide-articles, .slide-poems { background-position: 78% center; }
  .slide-articles { background-image: linear-gradient(rgba(15, 18, 32, 0.72), rgba(15, 18, 32, 0.72)), url("{{ '/assets/hero-articles.jpg' | relative_url }}"); }
  .slide-poems { background-image: linear-gradient(rgba(15, 18, 32, 0.72), rgba(15, 18, 32, 0.72)), url("{{ '/assets/hero-poems.jpg' | relative_url }}"); }
}
@media (prefers-reduced-motion: reduce) {
  .carousel.is-js .carousel-track { transition: none; }
}
</style>

<div class="carousel" id="hero-carousel" aria-roledescription="carousel" aria-label="Articles and poems">
  <div class="carousel-track">
    <section class="slide slide-articles" aria-roledescription="slide" aria-label="1 of 2">
      <h1>Learn advanced poetry techniques and use them in your own poems</h1>
      <p>Express your feelings in poetry in more than one way. Every technique is explained in simple words, with examples from my own poems.</p>
      <a class="btn" href="{{ '/articles/' | relative_url }}" aria-label="Explore the articles">Explore</a>
    </section>
    <section class="slide slide-poems" aria-roledescription="slide" aria-label="2 of 2">
      <h2>Read the poems behind the techniques</h2>
      <p>Original poems where negative capability, defamiliarization and perceptual reversal come to life.</p>
      <a class="btn" href="{{ '/poems/' | relative_url }}" aria-label="Explore the poems">Explore</a>
    </section>
  </div>
  <div class="carousel-controls">
    <button type="button" class="arrow prev" aria-label="Previous slide">&lsaquo;</button>
    <button type="button" class="dot" aria-label="Show slide 1"></button>
    <button type="button" class="dot" aria-label="Show slide 2"></button>
    <button type="button" class="arrow next" aria-label="Next slide">&rsaquo;</button>
  </div>
</div>

<script>
(function () {
  var c = document.getElementById("hero-carousel");
  if (!c) return;
  var track = c.querySelector(".carousel-track");
  var slides = c.querySelectorAll(".slide");
  var dots = c.querySelectorAll(".dot");
  var i = 0, timer;
  c.classList.add("is-js");
  function go(n) {
    i = (n + slides.length) % slides.length;
    track.style.transform = "translateX(-" + i * 100 + "%)";
    for (var k = 0; k < slides.length; k++) {
      if (k === i) { slides[k].removeAttribute("inert"); } else { slides[k].setAttribute("inert", ""); }
      dots[k].setAttribute("aria-current", k === i ? "true" : "false");
    }
  }
  function stop() { clearTimeout(timer); }
  go(0);
  if (!window.matchMedia("(prefers-reduced-motion: reduce)").matches) {
    timer = setTimeout(function () { go(1); }, 3000);
  }
  c.addEventListener("mouseenter", stop);
  c.addEventListener("focusin", stop);
  c.addEventListener("touchstart", stop, { passive: true });
  c.querySelector(".prev").addEventListener("click", function () { stop(); go(i - 1); });
  c.querySelector(".next").addEventListener("click", function () { stop(); go(i + 1); });
  for (var d = 0; d < dots.length; d++) {
    (function (n) { dots[n].addEventListener("click", function () { stop(); go(n); }); })(d);
  }
})();
</script>

<style>
.card.feature { position: relative; padding: 28px 24px 24px; border: 1px solid rgba(212,175,106,.28); border-radius: 14px; background: linear-gradient(180deg, rgba(212,175,106,.08), rgba(212,175,106,0) 70%); transition: transform .2s ease, border-color .2s ease, box-shadow .2s ease; }
.card.feature:hover { transform: translateY(-3px); border-color: #d4af6a; box-shadow: 0 10px 28px rgba(212,175,106,.12); }
.card.feature .num { position: absolute; top: 14px; right: 20px; font-family: "Playfair Display", Georgia, serif; font-size: 2.2em; font-weight: 700; line-height: 1; color: rgba(212,175,106,.28); }
.card.feature svg { display: block; width: 30px; height: 30px; margin-bottom: 14px; fill: none; stroke: #d4af6a; stroke-width: 1.6; stroke-linecap: round; stroke-linejoin: round; }
@media (max-width: 899px) { .landing-section .post-list > li { margin-bottom: 16px; } }
.landing-section .post-list .tag { display: flex; align-items: center; gap: 8px; font-size: .75em; letter-spacing: .14em; text-transform: uppercase; color: #d4af6a; }
.landing-section .post-list .tag svg { width: 16px; height: 16px; fill: none; stroke: currentColor; stroke-width: 1.8; stroke-linecap: round; stroke-linejoin: round; }
.landing-section .post-list .excerpt { margin: 10px 0 0; font-size: .92em; line-height: 1.6; opacity: .8; }
.landing-section .post-list > li.card-article { padding: 22px; border: 1px solid rgba(128,128,128,.28); border-top: 3px solid #d4af6a; border-radius: 12px; background: #141831; }
.landing-section .post-list > li.card-poem { padding: 40px 24px 26px; text-align: center; border: 1px solid rgba(212,175,106,.3); border-radius: 90px 90px 14px 14px; background: radial-gradient(ellipse at 50% 0%, rgba(212,175,106,.16), rgba(212,175,106,0) 70%), #121629; }
.landing-section .post-list > li.card-poem .tag { justify-content: center; }
.landing-section .post-list > li.card-poem .excerpt { font-style: italic; }
@media (prefers-reduced-motion: reduce) { .card.feature { transition: none; } .card.feature:hover { transform: none; } }
</style>
<div class="landing-section">
  <h2>What you will find here</h2>
  <div class="cards">
    <div class="card feature"><span class="num">01</span><svg viewBox="0 0 24 24" aria-hidden="true"><path d="M12 3l1.8 5.2L19 10l-5.2 1.8L12 17l-1.8-5.2L5 10l5.2-1.8z"/><path d="M19 16l.7 1.8 1.8.7-1.8.7L19 21l-.7-1.8-1.8-.7 1.8-.7z"/></svg><h3>Advanced techniques</h3><p>Perception-based methods such as negative capability, the objective correlative and defamiliarization.</p></div>
    <div class="card feature"><span class="num">02</span><svg viewBox="0 0 24 24" aria-hidden="true"><path d="M4 5h6a3 3 0 0 1 2 1 3 3 0 0 1 2-1h6v13h-6a3 3 0 0 0-2 1 3 3 0 0 0-2-1H4z"/><path d="M12 6v13"/></svg><h3>Simple explanations</h3><p>Each method in plain words, so you can understand it and try it the same day.</p></div>
    <div class="card feature"><span class="num">03</span><svg viewBox="0 0 24 24" aria-hidden="true"><path d="M20.2 3.8C13 3 8 8 7 15l-3 5"/><path d="M20.2 3.8c.8 7.2-4.2 12.2-11.2 12.2"/><path d="M9 15l6-6"/></svg><h3>Examples from my poems</h3><p>See every technique at work in lines from my own poetry.</p></div>
  </div>
</div>
<div class="landing-section">
  <h2>Latest articles</h2>
  <ul class="post-list">
  {% for post in site.posts limit:3 %}
    <li class="card-article">
      <span class="tag"><svg viewBox="0 0 24 24" aria-hidden="true"><path d="M3 21l3.5-1 11-11-2.5-2.5-11 11z"/><path d="M14.5 6.5L17 9"/></svg>Article</span>
      <h3><a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a></h3>
      <p class="excerpt">{{ post.description | default: post.excerpt | strip_html | strip | truncate: 130 }}</p>
    </li>
  {% endfor %}
  </ul>
  <p><a href="{{ '/articles/' | relative_url }}">See all articles &rarr;</a></p>
</div>
<div class="landing-section">
  <h2>Latest poems</h2>
  <ul class="post-list">
  {% assign latest_poems = site.poems | sort: "date" | reverse %}
  {% for poem in latest_poems limit:3 %}
    <li class="card-poem">
      <span class="tag"><svg viewBox="0 0 24 24" aria-hidden="true"><g fill="currentColor" stroke="none"><path d="M11 11C9.5 7 5.5 4 1.5 4.5 1.5 8 3 12 8 13.5 9.5 13.5 10.5 12.5 11 11z"/><path d="M11 13.5C8.5 14.5 5.8 16 6.5 19.5 9 19.5 11 17.5 11 13.5z" opacity=".5"/><g transform="translate(24 0) scale(-1 1)"><path d="M11 11C9.5 7 5.5 4 1.5 4.5 1.5 8 3 12 8 13.5 9.5 13.5 10.5 12.5 11 11z"/><path d="M11 13.5C8.5 14.5 5.8 16 6.5 19.5 9 19.5 11 17.5 11 13.5z" opacity=".5"/></g></g></svg>Poem</span>
      <h3><a class="post-link" href="{{ poem.url | relative_url }}">{{ poem.title | escape }}</a></h3>
      <p class="excerpt">{{ poem.description | strip_html | strip | truncate: 130 }}</p>
    </li>
  {% endfor %}
  </ul>
  <p><a href="{{ '/poems/' | relative_url }}">See all poems &rarr;</a></p>
</div>
<div class="closing">
  <h2>Ready to try a new technique?</h2>
  <p>Read the articles and find techniques to apply in your poetry right now!</p>
  <a class="btn" href="{{ '/articles/' | relative_url }}">Start reading</a>
</div>
