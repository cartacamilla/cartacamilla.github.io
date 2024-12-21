---
layout: default
title: Welcome
---

<div class="home-intro">
  <div class="container">
    <h1>Camilla Carta | Digital Project Manager</h1>
    <p>Welcome to my site! </p>
    <p>I specialize in delivering cutting-edge digital solutions for businesses, blending project management expertise with technical know-how. Explore my portfolio, read my blog, or get in touch!</p>
    <div class="intro-buttons">
      <a href="#portfolio" class="btn btn-primary">View Portfolio</a>
      <a href="/contact/" class="btn btn-secondary">Contact Me</a>
    </div>
  </div>
</div>

<hr class="divider">

<div id="portfolio" class="portfolio-section">
  <div class="container">
    <h2>My Portfolio</h2>
    <div class="portfolio-items">
      <div class="portfolio-item">
        <h3><a href="#">Eye-Tracking Product Demonstrator</a></h3>
        <p>A cutting-edge project using state-of-the-art sensing technology for AR and robotics.</p>
      </div>
      <div class="portfolio-item">
        <h3><a href="#">AR/Robotics Demonstrator</a></h3>
        <p>Delivering innovative solutions for augmented reality and robotic systems.</p>
      </div>
      <div class="portfolio-item">
        <h3><a href="#">3D Face Reconstruction</a></h3>
        <p>Research and development of a deep learning algorithm for 3D face modeling.</p>
      </div>
    </div>
  </div>
</div>

<hr class="divider">

<div id="blog" class="blog-section">
  <div class="container">
    <h2>Recent Blog Posts</h2>
    <ul class="blog-list">
      {% for post in site.posts limit: 5 %}
      <li>
        <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
        <p>{{ post.excerpt | strip_html | truncate: 150 }}</p>
        <small>Published on {{ post.date | date: "%b %d, %Y" }}</small>
      </li>
      {% endfor %}
    </ul>
    <a href="/blog" class="btn btn-secondary">View All Posts</a>
  </div>
</div>
