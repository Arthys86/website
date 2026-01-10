---
layout: page
title: "Gallery"
subtitle: "Gallery subtitle"
permalink: /gallery/
---

<div id="custom-gallery-container">
  <style>
    /* 1. Academic Filter Tags */
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

    /* 2. Mode 1: Balanced Staggered Grid (For "All") */
    #custom-gallery-container .gallery-grid.staggered-mode {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      grid-auto-rows: 10px; /* 基础栅格高度 */
      grid-auto-flow: dense;
      gap: 20px;
    }

    #custom-gallery-container .staggered-mode .gallery-item {
      grid-row: span 25; /* 默认跨度 */
      margin-bottom: 0;
    }
    /* 模拟有序错位：根据图片特性（手动或动态）设置不同跨度 */
    #custom-gallery-container .staggered-mode .gallery-item:nth-child(even) { grid-row: span 35; }
    #custom-gallery-container .staggered-mode .gallery-item:nth-child(3n) { grid-row: span 30; }

    /* 3. Mode 2: Center Original Style (For "Characters") */
    #custom-gallery-container .gallery-grid.center-mode {
      display: flex;
      flex-direction: column;
      align-items: center; /* 整体居中 */
      gap: 40px;
    }

    #custom-gallery-container .center-mode .gallery-item {
      width: auto;
      max-width: 90%;
      height: auto;
    }

    #custom-gallery-container .center-mode .gallery-item img {
      width: auto;
      max-width: 100%;
      height: auto; /* 保持原始比例 */
      border-radius: 4px;
    }

    /* 4. Mode 3: Horizontal Mode (For History/Artifacts) */
    #custom-gallery-container .gallery-grid.horizontal-mode {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      justify-content: center;
    }

    #custom-gallery-container .horizontal-mode .gallery-item {
      height: 250px;
      flex: 0 0 auto;
    }

    #custom-gallery-container .horizontal-mode .gallery-item img {
      height: 100%;
      width: auto;
    }

    /* Common Item Styles - NO BORDERS/WHITE EDGES */
    #custom-gallery-container .gallery-item {
      position: relative;
      overflow: hidden;
      background: none; /* 去掉白边和背景 */
      transition: transform 0.3s ease, opacity 0.3s ease;
    }

    #custom-gallery-container .gallery-item img {
      display: block;
      transition: transform 0.6s ease;
    }

    /* Overlay Info */
    #custom-gallery-container .gallery-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: linear-gradient(to top, rgba(0,0,0,0.8) 0%, transparent 100%);
      color: #fff;
      padding: 40px 15px 15px 15px;
      opacity: 0;
      transform: translateY(10px);
      transition: all 0.3s ease;
      pointer-events: none;
    }

    #custom-gallery-container .gallery-item:hover .gallery-overlay {
      opacity: 1;
      transform: translateY(0);
    }

    #custom-gallery-container .gallery-item:hover img { transform: scale(1.03); }

    .overlay-title { font-size: 0.9rem; font-weight: 600; display: block; }
    .overlay-desc { font-size: 0.75rem; opacity: 0.8; }

    #custom-gallery-container .gallery-item.hide { display: none !important; }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">All</span>
    <span class="filter-tag" data-filter="history">History</span>
    <span class="filter-tag" data-filter="characters">Characters</span>
    <span class="filter-tag" data-filter="artifacts">Artifacts</span>
  </div>

  <div class="gallery-grid staggered-mode" id="gallery-grid">
    
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
        <span class="overlay-desc">The Rogue Prince</span>
      </div>
    </div>

    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/pi.jpg" alt="PI">
      <div class="gallery-overlay">
        <span class="overlay-title">PI</span>
        <span class="overlay-desc">Principal Investigator</span>
      </div>
    </div>

    <div class="gallery-item" data-category="history">
      <img src="{{ site.baseurl }}/assets/img/the-conquest.jpg" alt="The Conquest">
      <div class="gallery-overlay">
        <span class="overlay-title">The Conquest</span>
        <span class="overlay-desc">Visenya Targaryen and Vhagar</span>
      </div>
    </div>

    <div class="gallery-item" data-category="artifacts">
      <img src="{{ site.baseurl }}/assets/img/darksister.jpeg" alt="Dark Sister">
      <div class="gallery-overlay">
        <span class="overlay-title">Dark Sister</span>
        <span class="overlay-desc">Valyrian steel longsword</span>
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

          // Switch Layout Modes
          grid.classList.remove('staggered-mode', 'center-mode', 'horizontal-mode');
          
          if (selectedFilter === 'all') {
            grid.classList.add('staggered-mode');
          } else if (selectedFilter === 'characters') {
            grid.classList.add('center-mode');
          } else {
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
