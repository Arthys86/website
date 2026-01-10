---
layout: page
title: "Gallery"
subtitle: "Gallery subtitle"
permalink: /gallery/
---

<div id="custom-gallery-container">
  <style>
    /* 1. Filter Tags - Colors Corrected */
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

    /* 2. Layout Containers */
    #custom-gallery-container .gallery-grid {
      display: flex;
      flex-wrap: wrap;
      gap: 20px;
      transition: all 0.4s ease;
    }

    /* --- Mode: All (Balanced Staggered Grid) --- */
    #custom-gallery-container .gallery-grid.mode-all {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      grid-auto-rows: 10px; /* 控制错位的精细度 */
      gap: 20px;
    }

    #custom-gallery-container .mode-all .gallery-item {
      display: block;
      grid-row-end: span 25; /* 默认跨度 */
    }
    /* 让奇数列或特定项目产生高度错位感 */
    #custom-gallery-container .mode-all .gallery-item:nth-child(even) {
      margin-top: 30px;
    }

    /* --- Mode: Characters (Justified Center) --- */
    #custom-gallery-container .gallery-grid.mode-characters {
      display: flex;
      justify-content: center; /* 整体居中 */
      align-items: flex-start;
      flex-wrap: wrap;
    }

    #custom-gallery-container .mode-characters .gallery-item {
      flex: 0 1 auto;
      max-width: 30%; /* 保证一行约3张，可根据喜好调整 */
      height: auto;
    }

    #custom-gallery-container .mode-characters .gallery-item img {
      width: 100%;
      height: auto; /* 保证原比例缩放，不留白边 */
      object-fit: contain;
    }

    /* --- Mode: History & Artifacts (Horizontal Row) --- */
    #custom-gallery-container .gallery-grid.mode-horizontal {
      display: flex;
      flex-direction: row;
      justify-content: flex-start;
    }

    #custom-gallery-container .mode-horizontal .gallery-item {
      height: 280px;
      flex: 0 0 auto;
    }

    #custom-gallery-container .mode-horizontal .gallery-item img {
      height: 100%;
      width: auto;
      object-fit: contain; /* 不裁剪 */
    }

    /* Common Item Styles */
    #custom-gallery-container .gallery-item {
      position: relative;
      border-radius: 10px;
      overflow: hidden;
      background-color: transparent; /* 去掉背景白边 */
      transition: transform 0.3s ease, opacity 0.3s ease;
    }

    #custom-gallery-container .gallery-item img {
      display: block;
      transition: transform 0.6s ease;
    }

    #custom-gallery-container .gallery-item.hide { display: none !important; }

    /* Overlay - Original Style */
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
      transition: all 0.4s ease;
      pointer-events: none;
    }

    #custom-gallery-container .gallery-item:hover .gallery-overlay { opacity: 1; transform: translateY(0); }
    #custom-gallery-container .gallery-item:hover img { transform: scale(1.04); }

    .overlay-title { font-size: 1rem; font-weight: 600; display: block; }
    .overlay-desc { font-size: 0.8rem; opacity: 0.9; }

    @media (max-width: 768px) {
      #custom-gallery-container .mode-characters .gallery-item { max-width: 45%; }
      #custom-gallery-container .mode-horizontal .gallery-item { height: 200px; }
    }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">All</span>
    <span class="filter-tag" data-filter="history">History</span>
    <span class="filter-tag" data-filter="characters">Characters</span>
    <span class="filter-tag" data-filter="artifacts">Artifacts</span>
  </div>

  <div class="gallery-grid mode-all" id="gallery-grid">
    
    <div class="gallery-item" data-category="characters">
      <img src="{{ site.baseurl }}/assets/img/pi.jpg" alt="PI">
      <div class="gallery-overlay">
        <span class="overlay-title">Principal Investigator</span>
        <span class="overlay-desc">Project Lead and Researcher</span>
      </div>
    </div>

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

          // Reset grid classes
          grid.className = 'gallery-grid';

          // Apply specific mode classes
          if (selectedFilter === 'all') {
            grid.classList.add('mode-all');
          } else if (selectedFilter === 'characters') {
            grid.classList.add('mode-characters');
          } else {
            grid.classList.add('mode-horizontal');
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
