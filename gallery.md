---
layout: page
title: "Gallery"
subtitle: "Gallery subtitle"
permalink: /gallery/
---

<div id="custom-gallery-container">
  <style>
    /* 1. Filter Navigation Styling */
    #custom-gallery-container .gallery-filters {
      display: flex;
      gap: 20px;
      margin: 20px 0 40px 0;
      border-bottom: 1px solid #eee;
      padding-bottom: 15px;
    }

    #custom-gallery-container .filter-tag {
      font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace;
      font-size: 1rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      cursor: pointer;
      color: #003366; 
      padding: 5px 5px;
      transition: all 0.3s ease;
      position: relative;
    }

    /* Hover State: Light Gold */
    #custom-gallery-container .filter-tag:hover { color: #D4AF37; }
    /* Active State: Deep Gold */
    #custom-gallery-container .filter-tag.active { font-weight: bold; color: #996600; }
    #custom-gallery-container .filter-tag.active::after {
      content: '';
      position: absolute;
      bottom: -16px;
      left: 0;
      width: 100%;
      height: 3px;
      background: #996600;
    }

    /* 2. Layout Modes Configuration */
    
    /* Common: No background, no cropping, proportional scaling */
    #custom-gallery-container .gallery-item {
      position: relative;
      border-radius: 10px;
      overflow: hidden;
      background: transparent !important;
      transition: transform 0.3s ease, opacity 0.3s ease;
    }

    #custom-gallery-container .gallery-item img {
      display: block;
      width: 100%;
      height: auto;
      object-fit: contain; 
    }

    /* [All] & [Masonry]: Column-based Waterfall */
    #custom-gallery-container .gallery-grid.mode-masonry {
      column-count: 3;
      column-gap: 20px;
      display: block;
    }
    #custom-gallery-container .mode-masonry .gallery-item {
      break-inside: avoid;
      display: inline-block;
      width: 100%;
      margin-bottom: 20px;
      height: auto; 
    }

    /* [Left]: Horizontal Row with Fixed Height */
    #custom-gallery-container .gallery-grid.mode-left {
      display: flex;
      flex-wrap: wrap;
      justify-content: flex-start;
      gap: 15px;
    }
    #custom-gallery-container .mode-left .gallery-item {
      height: 250px;
      width: auto;
      flex: 0 0 auto;
    }
    #custom-gallery-container .mode-left .gallery-item img {
      height: 100%;
      width: auto;
    }

    /* [Centered]: Proportional Scaling with Center Alignment */
    #custom-gallery-container .gallery-grid.mode-centered {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 30px;
    }
    #custom-gallery-container .mode-centered .gallery-item {
      flex: 0 1 320px; 
      height: auto;
    }

    /* 3. Overlay and Captions */
    #custom-gallery-container .gallery-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, rgba(0,0,0,0.3) 100%);
      color: #fff;
      padding: 40px 15px 15px 15px;
      opacity: 0;
      transform: translateY(10px);
      transition: all 0.3s ease;
      pointer-events: none;
    }
    #custom-gallery-container .gallery-item:hover .gallery-overlay { opacity: 1; transform: translateY(0); }
    #custom-gallery-container .gallery-item:hover img { transform: scale(1.03); }

    .overlay-title { font-size: 0.95rem; font-weight: 600; display: block; }
    .overlay-desc { font-size: 0.75rem; opacity: 0.8; }

    #custom-gallery-container .gallery-item.hide { display: none !important; }

    /* Responsive adjustments */
    @media (max-width: 900px) {
      #custom-gallery-container .gallery-grid.mode-masonry { column-count: 2; }
    }
    @media (max-width: 600px) {
      #custom-gallery-container .gallery-grid.mode-masonry { column-count: 1; }
    }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">All</span>
    <span class="filter-tag" data-filter="left">Left</span>
    <span class="filter-tag" data-filter="centered">Centered</span>
    <span class="filter-tag" data-filter="masonry">Masonry</span>
  </div>

  <div class="gallery-grid mode-masonry" id="gallery-grid">
    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/pi.jpg" alt="PI">
      <div class="gallery-overlay">
        <span class="overlay-title">Principal Investigator</span>
        <span class="overlay-desc">Project Lead</span>
      </div>
    </div>

    <div class="gallery-item" data-category="history">
      <img src="{{ site.baseurl }}/assets/img/dotd.png" alt="History 1">
      <div class="gallery-overlay">
        <span class="overlay-title">Dance of the Dragons</span>
        <span class="overlay-desc">Historical Record</span>
      </div>
    </div>

    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/placeholder-member.jpg" alt="Member">
      <div class="gallery-overlay">
        <span class="overlay-title">Team Member</span>
        <span class="overlay-desc">Researcher</span>
      </div>
    </div>

    <div class="gallery-item" data-category="history">
      <img src="{{ site.baseurl }}/assets/img/the-conquest.jpg" alt="History 2">
      <div class="gallery-overlay">
        <span class="overlay-title">The Conquest</span>
        <span class="overlay-desc">Archival Image</span>
      </div>
    </div>

    <div class="gallery-item" data-category="artifacts">
      <img src="{{ site.baseurl }}/assets/img/darksister.jpeg" alt="Artifact 1">
      <div class="gallery-overlay">
        <span class="overlay-title">Dark Sister</span>
        <span class="overlay-desc">Ancient Artifact</span>
      </div>
    </div>

    <div class="gallery-item" data-category="artifacts">
      <img src="{{ site.baseurl }}/assets/img/it.jpg" alt="Artifact 2">
      <div class="gallery-overlay">
        <span class="overlay-title">Iron Throne</span>
        <span class="overlay-desc">Relic Analysis</span>
      </div>
    </div>
  </div>

  <script>
    document.addEventListener("DOMContentLoaded", function() {
      const filters = document.querySelectorAll('#custom-gallery-container .filter-tag');
      const items = document.querySelectorAll('#custom-gallery-container .gallery-item');
      const grid = document.getElementById('gallery-grid');

      filters.forEach(filter => {
        filter.addEventListener('click', function() {
          filters.forEach(f => f.classList.remove('active'));
          this.classList.add('active');
          const selectedFilter = this.getAttribute('data-filter');

          /* Reset layout modes */
          grid.className = 'gallery-grid';
          
          if (selectedFilter === 'all' || selectedFilter === 'masonry') {
            grid.classList.add('mode-masonry');
          } else if (selectedFilter === 'left') {
            grid.classList.add('mode-left');
          } else if (selectedFilter === 'centered') {
            grid.classList.add('mode-centered');
          }

          items.forEach(item => {
            /* Show all images for every filter as requested */
            item.classList.remove('hide');
            item.style.opacity = "0";
            setTimeout(() => { item.style.opacity = "1"; }, 50);
          });
        });
      });
    });
  </script>
</div>
