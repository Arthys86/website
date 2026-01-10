---
layout: page
title: "Gallery"
subtitle: "Gallery subtitle"
permalink: /gallery/
---

<style>
  /* Filter Tags Styling */
  .gallery-filters {
    display: flex;
    gap: 10px;
    margin-bottom: 30px;
    flex-wrap: wrap;
  }

  .filter-tag {
    padding: 6px 16px;
    border-radius: 20px;
    background: #f0f0f0;
    font-size: 0.9rem;
    cursor: pointer;
    border: 1px solid #ddd;
    transition: all 0.3s ease;
  }

  .filter-tag:hover, .filter-tag.active {
    background: #333;
    color: #fff;
    border-color: #333;
  }

  /* Masonry Column Layout */
  .gallery-columns {
    column-count: 3;
    column-gap: 20px;
    padding: 10px 0;
  }

  @media (max-width: 900px) { .gallery-columns { column-count: 2; } }
  @media (max-width: 600px) { .gallery-columns { column-count: 1; } }

  .gallery-item {
    break-inside: avoid;
    margin-bottom: 20px;
    position: relative;
    border-radius: 8px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0,0,0,0.08);
    transition: transform 0.3s ease;
  }

  .gallery-item:hover {
    transform: translateY(-5px);
  }

  .gallery-item img {
    width: 100%;
    height: auto; /* Maintains original aspect ratio */
    display: block;
  }

  /* Text Overlay on Hover */
  .gallery-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.6);
    color: white;
    opacity: 0;
    transition: opacity 0.3s ease;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 20px;
    text-align: center;
  }

  .gallery-item:hover .gallery-overlay {
    opacity: 1;
  }

  .item-title {
    font-size: 1.1rem;
    font-weight: 600;
    margin-bottom: 8px;
    border-bottom: 1px solid rgba(255,255,255,0.4);
    padding-bottom: 4px;
  }

  .item-desc {
    font-size: 0.85rem;
    line-height: 1.4;
  }
</style>

<div class="gallery-filters">
  <div class="filter-tag active">All</div>
  <div class="filter-tag">Research</div>
  <div class="filter-tag">Team</div>
  <div class="filter-tag">Events</div>
</div>

<div class="gallery-columns">

  <div class="gallery-item">
    <img src="/assets/img/placeholder-member.jpg" alt="Member photo">
    <div class="gallery-overlay">
      <div class="item-title">Member Profile</div>
      <div class="item-desc">High-resolution capture of team structure and individual research focus areas.</div>
    </div>
  </div>

  <div class="gallery-item">
    <img src="/assets/img/the-conquest.jpg" alt="Landscape achievement">
    <div class="gallery-overlay">
      <div class="item-title">Field Work</div>
      <div class="item-desc">Overview of experimental setups and large-scale data collection results.</div>
    </div>
  </div>

  <div class="gallery-item">
    <img src="/assets/img/dotd.png" alt="Portrait detail">
    <div class="gallery-overlay">
      <div class="item-title">Structural Analysis</div>
      <div class="item-desc">Vertical profiling of micro-electronic components and substrate integration.</div>
    </div>
  </div>

  <div class="gallery-item">
    <img src="/assets/img/the-conquest.jpg" alt="Lab view">
    <div class="gallery-overlay">
      <div class="item-title">Collaborative Space</div>
      <div class="item-desc">Internal laboratory environment optimized for soft electronics prototyping.</div>
    </div>
  </div>

  <div class="gallery-item">
    <img src="/assets/img/placeholder-member.jpg" alt="Group session">
    <div class="gallery-overlay">
      <div class="item-title">Seminar Session</div>
      <div class="item-desc">Weekly technical discussions regarding wireless sensing signal processing.</div>
    </div>
  </div>

</div>

<script>
  /* Basic Filter Interaction Logic */
  document.querySelectorAll('.filter-tag').forEach(tag => {
    tag.addEventListener('click', function() {
      document.querySelector('.filter-tag.active').classList.remove('active');
      this.classList.add('active');
      /* Implementation for actual filtering logic can be added here */
    });
  });
</script>
