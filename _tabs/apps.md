---
layout: page
title: Apps
icon: fas fa-th-large
order: 4
description: Independent apps and games created by Victor da Cruz Amaro.
---

<p class="apps-intro">
  A growing collection of apps and games I have designed and built. More projects will join the gallery over time.
</p>

<div class="app-gallery" aria-label="Apps and games">
  {% for app in site.data.apps %}
    <article class="app-card">
      <a
        class="app-card-link"
        href="{{ app.app_store_url }}"
        target="_blank"
        rel="noopener noreferrer"
        aria-label="View {{ app.name }} on the App Store"
      >
        <div
          class="app-card-visual"
          role="img"
          aria-label="{{ app.cover_alt }}"
          style="--app-cover: url('{{ app.cover | relative_url }}')"
        >
          <span class="app-status">Available now</span>
        </div>

        <div class="app-card-body">
          <div class="app-card-heading">
            <span
              class="app-card-icon"
              aria-hidden="true"
              style="--app-icon: url('{{ app.icon | relative_url }}')"
            ></span>
            <div>
              <h2>{{ app.name }}</h2>
              <p class="app-tagline">{{ app.tagline }}</p>
            </div>
          </div>

          <p class="app-description">{{ app.description }}</p>

          <ul class="app-platforms" aria-label="Available platforms">
            {% for platform in app.platforms %}
              <li>{{ platform }}</li>
            {% endfor %}
          </ul>

          <span class="app-card-cta">
            <i class="fab fa-apple" aria-hidden="true"></i>
            View on the App Store
            <i class="fas fa-arrow-up-right-from-square" aria-hidden="true"></i>
          </span>
        </div>
      </a>
    </article>
  {% endfor %}
</div>
