---
layout: page
title: "Gallery"
subtitle: "Collection of Scientific Records & Artifacts"
permalink: /gallery/
---

<div id="custom-gallery-container">
  <style>
    /* Academic Filter Tags */
    #custom-gallery-container .gallery-filters {
      display: flex;
      gap: 15px;
      margin: 20px 0 40px 0;
      border-bottom: 1px solid #eee;
      padding-bottom: 15px;
    }

    #custom-gallery-container .filter-tag {
      font-family: "SFMono-Regular", Consolas, "Liberation Mono", Menlo, monospace; /* Academic Mono Font */
      font-size: 0.75rem;
      text-transform: uppercase;
      letter-spacing: 1px;
      cursor: pointer;
      color: #003366; /* UST Deep Blue */
      padding: 5px 10px;
      transition: all 0.2s ease;
      position: relative;
    }

    #custom-gallery-container .filter-tag.active {
      font-weight: bold;
      color: #D4AF37; /* UST Gold */
    }

    #custom-gallery-container .filter-tag.active::after {
      content: '';
      position: absolute;
      bottom: -16px;
      left: 0;
      width: 100%;
      height: 3px;
      background: #D4AF37;
    }

    /* Layout Transitions */
    #custom-gallery-container .gallery-grid {
      transition: all 0.5s ease-in-out;
    }

    /* Mode 1: Academic Masonry (For "All") */
    #custom-gallery-container .gallery-grid.masonry-mode {
      column-count: 3;
      column-gap: 25px;
      display: block;
    }

    #custom-gallery-container .masonry-mode .gallery-item {
      break-inside: avoid;
      display: inline-block;
      width: 100%;
      margin-bottom: 25px;
      border: 1px solid #eee; /* Archive box look */
      padding: 10px;
      background: #fff;
    }

    /* Mode 2: Horizontal Row (For Categories) - NO CROPPING */
    #custom-gallery-container .gallery-grid.horizontal-mode {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
    }

    #custom-gallery-container .horizontal-mode .gallery-item {
      flex: 0 0 auto;
      height: 300px; /* Fixed standard height for rows */
      border: 1px solid #eee;
      padding: 10px;
      background: #fff;
    }

    #custom-gallery-container .horizontal-mode .gallery-item img {
      width: auto;
      height: 100%;
      object-fit: contain; /* Guarantee no cropping */
    }

    /* Common Academic Item Styling */
    #custom-gallery-container .gallery-item {
      position: relative;
      box-shadow: 0 2px 8px rgba(0,0,0,0.03);
      transition: box-shadow 0.3s ease;
    }

    #custom-gallery-container .gallery-item:hover {
      box-shadow: 0 5px 15px rgba(0,0,0,0.1);
    }

    #custom-gallery-container .gallery-item img {
      display: block;
      max-width: 100%;
    }

    /* Academic Caption (No longer an overlay that blocks the image) */
    #custom-gallery-container .gallery-info {
      margin-top: 10px;
      border-top: 1px solid #f5f5f5;
      padding-top: 8px;
    }

    .item-label {
      font-family: monospace;
      font-size: 0.65rem;
      color: #999;
      display: block;
    }

    .item-title {
      font-size: 0.9rem;
      font-weight: 600;
      color: #333;
      margin: 2px 0;
    }

    .item-desc {
      font-size: 0.75rem;
      color: #666;
      line-height: 1.4;
    }

    #custom-gallery-container .gallery-item.hide { display: none !important; }

    @media (max-width: 800px) {
      #custom-gallery-container .gallery-grid.masonry-mode { column-count: 2; }
      #custom-gallery-container .horizontal-mode .gallery-item { height: 200px; }
    }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">Index</span>
    <span class="filter-tag" data-filter="history">History</span>
    <span class="filter-tag" data-filter="characters">Characters</span>
    <span class="filter-tag" data-filter="artifacts">Artifacts</span>
  </div>

  <div class="gallery-grid masonry-mode" id="gallery-grid">
    
    <div class="gallery-item" data-category="history">
      <img src="{{ site.baseurl }}/assets/img/dotd.png" alt="Dance of the Dragons">
      <div class="gallery-info">
        <span class="item-label">REC_001</span>
        <div class="item-title">Dance of the Dragons</div>
        <div class="item-desc">The Dance over Shipbreaker Bay.</div>
      </div>
    </div>

    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/placeholder-member.jpg" alt="Daemon Targaryen">
      <div class="gallery-info">
        <span class="item-label">CHR_002</span>
        <div class="item-title">Daemon Targaryen</div>
        <div class="item-desc">The Rogue Prince, Commander of the City Watch.</div>
      </div>
    </div>

    <div class="gallery-item" data-category="history">
      <img src="{{ site.baseurl }}/assets/img/the-conquest.jpg" alt="The Conquest">
      <div class="gallery-info">
        <span class="item-label">REC_003</span>
        <div class="item-title">The Conquest</div>
        <div class="item-desc">Visenya Targaryen and Vhagar.</div>
      </div>
    </div>

    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/pi.jpg" alt="Who">
      <div class="gallery-info">
        <span class="item-label">CHR_004</span>
        <div class="item-title">Who</div>
        <div class="item-desc">Identity unconfirmed. Data pending.</div>
      </div>
    </div>

    <div class="gallery-item" data-category="artifacts">
      <img src="{{ site.baseurl }}/assets/img/darksister.jpeg" alt="Dark Sister">
      <div class="gallery-info">
        <span class="item-label">ART_005</span>
        <div class="item-title">Dark Sister</div>
        <div class="item-desc">A longsword of Valyrian steel.</div>
      </div>
    </div>

    <div class="gallery-item" data-category="artifacts">
      <img src="{{ site.baseurl }}/assets/img/it.jpg" alt="Iron Throne">
      <div class="gallery-info">
        <span class="item-label">ART_006</span>
        <div class="item-title">Iron Throne</div>
        <div class="item-desc">The seat of the Lord of the Seven Kingdoms.</div>
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

          // Switch academic layout modes
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
