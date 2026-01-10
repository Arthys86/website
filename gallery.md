---
layout: page
title: "Gallery"
subtitle: "Gallery subtitle"
permalink: /gallery/
---

<div id="custom-gallery-container">
  <style>
    /* 1. 导航栏样式 - 保持您的颜色要求 */
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
      color: #003366; /* 默认深蓝 */
      padding: 5px 5px;
      transition: all 0.3s ease;
      position: relative;
    }

    #custom-gallery-container .filter-tag:hover { color: #D4AF37; } /* 悬停浅金 */
    #custom-gallery-container .filter-tag.active { font-weight: bold; color: #996600; } /* 选中深金 */
    #custom-gallery-container .filter-tag.active::after {
      content: '';
      position: absolute;
      bottom: -16px;
      left: 0;
      width: 100%;
      height: 3px;
      background: #996600;
    }

    /* 2. 核心容器布局 */
    #custom-gallery-container .gallery-grid {
      transition: all 0.3s ease;
    }

    /* --- Mode: All (学术瀑布流 - 最稳妥的错位感) --- */
    #custom-gallery-container .gallery-grid.mode-all {
      column-count: 3;
      column-gap: 20px;
      display: block;
    }
    #custom-gallery-container .mode-all .gallery-item {
      break-inside: avoid;
      display: inline-block;
      width: 100%;
      margin-bottom: 20px;
    }

    /* --- Mode: Characters (居中展示 - 等比缩放无白边) --- */
    #custom-gallery-container .gallery-grid.mode-characters {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 30px;
    }
    #custom-gallery-container .mode-characters .gallery-item {
      flex: 0 1 300px; /* 固定一个大致宽度，高度自适应 */
      height: auto;
    }

    /* --- Mode: History & Artifacts (等高横排 - 不裁剪) --- */
    #custom-gallery-container .gallery-grid.mode-horizontal {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
    }
    #custom-gallery-container .mode-horizontal .gallery-item {
      height: 250px;
      flex: 0 0 auto;
    }
    #custom-gallery-container .mode-horizontal .gallery-item img {
      height: 100%;
      width: auto;
    }

    /* 3. 通用项目样式 */
    #custom-gallery-container .gallery-item {
      position: relative;
      border-radius: 10px;
      overflow: hidden;
      background: none; /* 彻底去掉白边背景 */
    }

    #custom-gallery-container .gallery-item img {
      display: block;
      width: 100%;
      height: auto;
      object-fit: contain; /* 绝对不裁剪 */
      transition: transform 0.6s ease;
    }

    #custom-gallery-container .gallery-item.hide { display: none !important; }

    /* 4. 遮罩层 (保持原有方式) */
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

    /* 响应式 */
    @media (max-width: 900px) {
      #custom-gallery-container .gallery-grid.mode-all { column-count: 2; }
    }
    @media (max-width: 600px) {
      #custom-gallery-container .gallery-grid.mode-all { column-count: 1; }
      #custom-gallery-container .mode-characters .gallery-item { flex: 0 1 100%; }
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

          // 清除旧模式并添加新模式
          grid.className = 'gallery-grid';
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
              setTimeout(() => { item.style.opacity = "1"; }, 50);
            } else {
              item.classList.add('hide');
            }
          });
        });
      });
    });
  </script>
</div>
