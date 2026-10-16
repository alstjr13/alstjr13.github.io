---
layout: splash
title: "Minsuk Seo — Research & Notes"
excerpt: "Exploring information systems, machine learning, and data-driven decisions. Projects and learning notes by Minsuk Seo."
classes: home-page
---

<section class="home-hero" aria-labelledby="intro-title">
  <div>
    <p class="eyebrow">Information systems · Data & decisions</p>
    <h1 id="intro-title">Minsuk Seo<span class="name-ko" lang="ko">서민석</span></h1>
    <p class="hero-lead">Exploring how data and technology inform better decisions.</p>
    <p class="hero-description">My interests span management information systems, machine learning, natural language processing, and optimization. This is a space for my projects and the things I learn along the way.</p>
    <div class="action-links">
      <a class="btn btn--primary" href="{{ '/project_show/' | relative_url }}">Explore projects <span aria-hidden="true">↗</span></a>
      <a class="text-link" href="{{ '/cv/' | relative_url }}">View CV <span aria-hidden="true">→</span></a>
    </div>
    <div class="hero-contact"><a href="mailto:ianmsseo@gmail.com">Email</a><span aria-hidden="true">/</span><a href="https://github.com/alstjr13">GitHub</a><span aria-hidden="true">/</span><a href="https://www.linkedin.com/in/minsuk-seo/">LinkedIn</a></div>
  </div>
  <figure class="hero-portrait">
    <img src="{{ '/assets/files/minsuk.jpeg' | relative_url }}" alt="Minsuk Seo" width="360" height="440" fetchpriority="high">
    <figcaption>Based in Seoul, South Korea</figcaption>
  </figure>
</section>

<section class="home-section" aria-labelledby="focus-title">
  <p class="eyebrow">Research interests</p>
  <h2 id="focus-title">Questions, methods, and applications.</h2>
  <div class="interest-grid">
    <div><span class="section-number" aria-hidden="true">01</span><h3>Information systems</h3><p>Understanding the role of technology and information in organizations and business decisions.</p></div>
    <div><span class="section-number" aria-hidden="true">02</span><h3>Machine learning & NLP</h3><p>Learning from data and text, from foundational models to retrieval-augmented generation.</p></div>
    <div><span class="section-number" aria-hidden="true">03</span><h3>Analytics & optimization</h3><p>Using statistical analysis, econometrics, and optimization to investigate practical problems.</p></div>
  </div>
</section>

<section class="home-section" aria-labelledby="work-title">
  <div class="section-heading"><div><p class="eyebrow">Selected work</p><h2 id="work-title">From questions to evidence.</h2></div><a class="text-link" href="{{ '/project_show/' | relative_url }}">All projects →</a></div>
  {% include selected-project.html %}
</section>

<section class="home-section" aria-labelledby="notes-title">
  <div class="section-heading"><div><p class="eyebrow">Learning in public</p><h2 id="notes-title">From my notebook.</h2></div><a class="text-link" href="{{ '/categories/' | relative_url }}">All notes →</a></div>
  <div class="note-grid">
    <article><p class="eyebrow">Natural language processing</p><h3><a href="{% post_url 2024-12-02-rag %}">Retrieval augmented generation</a></h3><p>Notes on connecting language models with information retrieval.</p></article>
    <article><p class="eyebrow">Statistical learning</p><h3><a href="{% post_url 2024-12-01-linear-regression %}">Linear regression</a></h3><p>A closer look at regression, estimation, and the mathematics behind the model.</p></article>
    <article><p class="eyebrow">Machine learning</p><h3><a href="{% post_url 2024-02-01-machinelearning-decision-tree %}">Decision trees</a></h3><p>Learning how tree-based models split data and make predictions.</p></article>
  </div>
</section>
