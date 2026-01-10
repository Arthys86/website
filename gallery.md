---
layout: page
title: "Gallery"
subtitle: "Gallery subtitle"
permalink: /gallery/
---

<div id="custom-gallery-container">
  <style>
    /* Academic Filter Tags with Corrected Color States */
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
      color: #003366; /* Default: UST Deep Blue */
      padding: 5px 5px;
      transition: all 0.3s ease;
      position: relative;
      border: none;
      background: none;
    }

    /* Hover state: Light Gold */
    #custom-gallery-container .filter-tag:hover {
      color: #D4AF37; 
    }

    /* Selected (Active) state: Deep Gold (#996600) */
    #custom-gallery-container .filter-tag.active {
      font-weight: bold;
      color: #996600; /* Deep Gold */
    }

    #custom-gallery-container .filter-tag.active::after {
      content: '';
      position: absolute;
      bottom: -16px;
      left: 0;
      width: 100%;
      height: 3px;
      background: #996600; /* Deep Gold underline */
    }

    /* Grid Layout Transitions */
    #custom-gallery-container .gallery-grid {
      transition: all 0.5s ease-in-out;
    }

    /* Mode 1: Masonry (For "All") */
    #custom-gallery-container .gallery-grid.masonry-mode {
      column-count: 3;
      column-gap: 15px;
      display: block;
    }

    #custom-gallery-container .masonry-mode .gallery-item {
      break-inside: avoid;
      display: inline-block;
      width: 100%;
      margin-bottom: 15px;
    }

    /* Mode 2: Horizontal (For Categories) - No Cropping */
    #custom-gallery-container .gallery-grid.horizontal-mode {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
    }

    #custom-gallery-container .horizontal-mode .gallery-item {
      flex: 0 0 auto;
      height: 280px; 
    }

    #custom-gallery-container .horizontal-mode .gallery-item img {
      width: auto;
      height: 100%;
      object-fit: contain;
    }

    /* Common Gallery Item Styles */
    #custom-gallery-container .gallery-item {
      background-color: #f8f9fa;
      border-radius: 10px;
      overflow: hidden;
      position: relative;
      transition: transform 0.3s ease, opacity 0.3s ease;
    }

    #custom-gallery-container .gallery-item.hide { display: none !important; }

    #custom-gallery-container .gallery-item img {
      display: block;
      max-width: 100%;
      transition: transform 0.6s ease;
    }

    /* Overlay Styles */
    #custom-gallery-container .gallery-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, rgba(0,0,0,0.4) 60%, transparent 100%);
      color: #fff;
      padding: 50px 15px 15px 15px;
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
      text-align: left;
      pointer-events: none;
    }

    #custom-gallery-container .gallery-item:hover .gallery-overlay {
      opacity: 1;
      transform: translateY(0);
    }

    #custom-gallery-container .gallery-item:hover img {
      transform: scale(1.06);
    }

    .overlay-title {
      font-size: 1rem;
      font-weight: 600;
      display: block;
      margin-bottom: 2px;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
    }

    .overlay-desc {
      font-size: 0.8rem;
      opacity: 0.9;
      line-height: 1.3;
    }

    @media (max-width: 900px) {
      #custom-gallery-container .gallery-grid.masonry-mode { column-count: 2; }
      #custom-gallery-container .horizontal-mode .gallery-item { height: 200px; }
    }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">All</span>
    <span class="filter-tag" data-filter="history">History</span>
    <span class="filter-tag" data-filter="characters">Characters</span>
    <span class="filter-tag" data-filter="artifacts">Artifacts</span>
  </div>

  <div class="gallery-grid masonry-mode" id="gallery-grid">
    <div class="gallery-item" data-category="history">
      <img src="{{ site.baseurl }}/assets/img/dotd.png" alt="Dance of the Dragons">
      <div class="gallery-overlay">
        <span class="overlay-title">Dance of the Dragons</span>
        <span class="overlay-desc">The Dance over Shipbreaker Bay</span>
      </div>
    </div>

    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/placeholder-member.jpg" alt="Daemon Targaryen">
      <div class="gallery-overlay">
        <span class="overlay-title">Daemon Targaryen</span>
        <span class="overlay-desc">The Rogue Prince, Commander of the City Watch</span>
      </div>
    </div>

    <div class="gallery-item" data-category="history">
      <img src="{{ site.baseurl }}/assets/img/the-conquest.jpg" alt="The Conquest">
      <div class="gallery-overlay">
        <span class="overlay-title">The Conquest</span>
        <span class="overlay-desc">Visenya Targaryen and Vhagar</span>
      </div>
    </div>

    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/pi.jpg" alt="Who">
      <div class="gallery-overlay">
        <span class="overlay-title">Who</span>
        <span class="overlay-desc">I don't know</span>
      </div>
    </div>

    <div class="gallery-item" data-category="artifacts">
      <img src="{{ site.baseurl }}/assets/img/darksister.jpeg" alt="Dark Sister">
      <div class="gallery-overlay">
        <span class="overlay-title">Dark Sister</span>
        <span class="overlay-desc">a longsword of Valyrian steel</span>
      </div>
    </div>

    <div class="gallery-item" data-category="artifacts">
      <img src="{{ site.baseurl }}/assets/img/it.jpg" alt="Iron Throne">
      <div class="gallery-overlay">
        <span class="overlay-title">Iron Throne</span>
        <span class="overlay-desc">The seat of the Lord of the Seven Kingdoms</span>
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

          if (selectedFilter === 'all') {
            grid.classList.remove('horizontal-mode');
            grid.classList.add('masonry-mode');
          } else {
            grid.classList.remove('masonry-mode');
            grid.classList.add('horizontal-mode');
          }

          items.forEach(item => {
            const category = item.getAttribute('data-category');
            if (selectedFilter === 'all' || category === selectedFilter) {
              item.classList.remove('hide');
              item.style.opacity = "0";
              setTimeout(() => { item.style.opacity = "1"; }, 10);
            } else {
              item.classList.add('hide');
            }
          });
        });
      });
    });
  </script>
</div>
