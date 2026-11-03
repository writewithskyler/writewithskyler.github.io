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
.slide-articles { background: radial-gradient(ellipse at 85% 15%, rgba(212, 175, 106, 0.22), transparent 55%), linear-gradient(135deg, #171c38, #0f1220); }
.slide-poems { background: linear-gradient(90deg, rgba(15, 18, 32, 0.95) 35%, rgba(15, 18, 32, 0.4)), url("{{ '/assets/phantom-sound.jpg' | relative_url }}") center / cover no-repeat; }
.slide h1, .slide h2 { margin: 0 0 16px; max-width: 17em; font-size: 2.1em; line-height: 1.2; }
.slide p { margin: 0 0 8px; max-width: 34em; font-size: 1.1em; opacity: 0.9; }
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
