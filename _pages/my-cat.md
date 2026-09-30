---
permalink: /my-life/cat/
title: "My Cat 🐱"
author_profile: true
---

[← Back to My Life]({{ '/my-life/' | relative_url }})

A small photo album of my orange cat, from tiny kitten to professional nap-taker. Click any photo to see it full size.

{% assign cat_photos = "01|Napping on a cardboard lounger in front of a map puzzle,02|Keeping a close eye on my water bottle,03|A tiny kitten sitting on the carpet,04|Out for a walk in a harness, held close on an autumn day,05|Curled up on the scratcher with one pink-padded paw in the air,06|An AI-imagined tennis partner at Wimbledon,07|An AI-imagined tennis partner mid-backhand" | split: "," %}
<div class="cat-gallery">
{% for entry in cat_photos %}{% assign parts = entry | split: "|" %}
  <figure>
    <a href="{{ '/images/cat/web/cat-' | append: parts[0] | append: '.jpg' | relative_url }}">
      <img src="{{ '/images/cat/web/cat-' | append: parts[0] | append: '-thumb.jpg' | relative_url }}" alt="{{ parts[1] }}" loading="lazy">
    </a>
    <figcaption>{{ parts[1] }}</figcaption>
  </figure>
{% endfor %}
</div>
