---
permalink: /my-life/cat/
title: "Cheese 🐱"
author_profile: true
---

[← Back to My Life]({{ '/my-life/' | relative_url }})

A small photo album of Cheese, my orange cat, from tiny kitten to professional nap-taker. Click any photo to see it full size.

<div class="cat-gallery">
{% for i in (1..7) %}{% capture n %}{% if i < 10 %}0{% endif %}{{ i }}{% endcapture %}
  <a href="{{ '/images/cat/web/cat-' | append: n | append: '.jpg' | relative_url }}">
    <img src="{{ '/images/cat/web/cat-' | append: n | append: '-thumb.jpg' | relative_url }}" alt="Photo {{ i }} of Cheese" loading="lazy">
  </a>
{% endfor %}
</div>
