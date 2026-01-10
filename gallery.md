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

    #custom-gallery-container .filter-tag:hover { color: #D4AF37; }
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

    /* 2. Common Gallery Item Styles */
    #custom-gallery-container .gallery-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      transition: all 0.4s ease;
    }

    #custom-gallery-container .gallery-item {
      position: relative;
      border-radius: 10px;
      overflow: hidden;
      background: transparent !important;
      transition: opacity 0.3s ease;
    }

    #custom-gallery-container .gallery-item img {
      display: block;
      width: 100%;
      height: 100%;
      object-fit: contain;
    }

    /* Overlay Captions */
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

    .overlay-title { font-size: 0.95rem; font-weight: 600; display: block; }
    .overlay-desc { font-size: 0.75rem; opacity: 0.8; }

    /* Layout Specific Adjustments via JS logic */
    .mode-centered { justify-content: center; align-items: center; }
    .mode-left { justify-content: flex-start; }
    .mode-all { justify-content: center; }

    #custom-gallery-container .gallery-item.hide { display: none !important; }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">All</span>
    <span class="filter-tag" data-filter="left">Left</span>
    <span class="filter-tag" data-filter="centered">Centered</span>
    <span class="filter-tag" data-filter="masonry">Masonry</span>
  </div>

  <div class="gallery-grid mode-all" id="gallery-grid">
    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/pi.jpg" alt="Who">
      <div class="gallery-overlay">
        <span class="overlay-title">Who</span>
        <span class="overlay-desc">I don't know</span>
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
      const filters = document.querySelectorAll('.filter-tag');
      const grid = document.getElementById('gallery-grid');
      const items = document.querySelectorAll('.gallery-item');

      function updateLayout(mode) {
        grid.className = 'gallery-grid mode-' + mode;
        
        items.forEach(item => {
          const img = item.querySelector('img');
          const ratio = img.naturalWidth / img.naturalHeight || 1;

          if (mode === 'all' || mode === 'left') {
            /* Dynamic Justified Layout Logic */
            item.style.flex = `${ratio * 100} 1 auto`;
            item.style.width = `${ratio * 250}px`;
            item.style.height = '250px';
          } else if (mode === 'centered') {
            /* Three-column centered logic */
            item.style.flex = '0 1 calc(33.333% - 30px)';
            item.style.width = 'auto';
            item.style.height = 'auto';
          } else if (mode === 'masonry') {
            /* Reset for Masonry handled by CSS column-count */
            item.style.flex = '';
            item.style.width = '';
            item.style.height = '';
          }
        });
      }

      filters.forEach(filter => {
        filter.addEventListener('click', function() {
          filters.forEach(f => f.classList.remove('active'));
          this.classList.add('active');
          updateLayout(this.getAttribute('data-filter'));
        });
      });

      /* Initial trigger after images load to get natural dimensions */
      window.onload = () => updateLayout('all');
    });
  </script>
</div>
