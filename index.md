---
layout: default
title: Repository Studio
description: Signal-rich portal for R-KL's public GitHub work.
---

{% assign total_stars = 0 %}
{% assign total_forks = 0 %}
{% for item in site.data.repos %}
  {% assign total_stars = total_stars | plus: item.stars %}
  {% assign total_forks = total_forks | plus: item.forks %}
{% endfor %}

<section class="hero">
  <p class="hero__eyebrow">GitHub portfolio</p>
  <h1>Repository radar for Richard K Lijur-KL.</h1>
  <p>
    A hand-curated look at the tools, experiments, and forks that currently sit across the
    GitHub organisation <strong>R-KL</strong>. Each card links straight to the source of truth so
    visitors can explore, clone, or follow along.
  </p>
  <div class="hero__links">
    <a class="primary" href="https://github.com/R-KL" target="_blank" rel="noreferrer">Visit profile</a>
    <a class="secondary" href="https://github.com/R-KL?tab=repositories" target="_blank" rel="noreferrer">Browse repositories</a>
  </div>
</section>

<section class="stats-grid" aria-label="Repository stats">
  <article class="stat-card">
    <h3>Projects curated</h3>
    <p>{{ site.data.repos | size }}</p>
  </article>
  <article class="stat-card">
    <h3>Total stars</h3>
    <p>{{ total_stars }}</p>
  </article>
  <article class="stat-card">
    <h3>Total forks</h3>
    <p>{{ total_forks }}</p>
  </article>
  <article class="stat-card">
    <h3>Snapshot date</h3>
    <p>{{ site.time | date: "%b %d, %Y" }}</p>
  </article>
</section>

<section class="repo-grid" aria-label="Repositories">
  {% for repo in site.data.repos %}
    {% include repo-card.html repo=repo %}
  {% endfor %}
</section>

{% assign focus_repo = site.data.repos | where: "status", "Active research" | first %}
{% if focus_repo %}
<section class="focus-panel">
  <h2>Current focus: {{ focus_repo.name }}</h2>
  <p>
    {{ focus_repo.description }} Recent work landed on {{ focus_repo.updated | date: "%b %d, %Y" }},
    and the project continues to evolve under the Active research track. Keep an eye on GitHub for
    fresh commits.
  </p>
</section>
{% endif %}
