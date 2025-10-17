---
layout: default
---

<article class="photos-index">
  <header>
    <h1 class="post-title">{{ page.title }}</h1>
  </header>

  {% if page.content %}
  <div class="intro-text">
    {{ content }}
  </div>
  {% endif %}

  <div class="photo-post-list">
    {% assign photos = site.photos | sort: "date" | reverse %}
    {% for photo in photos %}
      <div class="photo-summary">
        <h2><a href="{{ photo.url }}">{{ photo.title }}</a></h2>

        {% if photo.excerpt %}
          <p>{{ photo.excerpt | strip_html | truncate: 200 }}</p>
        {% elsif photo.description %}
          <p>{{ photo.description }}</p>
        {% endif %}

        <p class="photo-date">{{ photo.date | date: "%B %d, %Y" }}</p>
      </div>
    {% endfor %}
  </div>
</article>

<style>
.photos-index {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.intro-text {
  margin-bottom: 2rem;
  line-height: 1.6;
  color: #555;
  text-align: center;
}

.photo-post-list {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.photo-summary h2 {
  font-size: 1.3rem;
  margin-bottom: 0.25rem;
}

.photo-summary a {
  text-decoration: none;
  color: var(--link-color, #0366d6);
}

.photo-summary a:hover {
  text-decoration: underline;
}

.photo-summary p {
  margin: 0.25rem 0;
  color: #555;
}

.photo-date {
  font-size: 0.9rem;
  color: #999;
}
</style>
`
