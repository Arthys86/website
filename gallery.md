---
layout: page
title: "Gallery"
subtitle: "Gallery subtitle"
permalink: /gallery/
---

<div id="custom-gallery-container">
  <style>
    /* Filter Tags Styling */
    #custom-gallery-container .gallery-filters {
      display: flex;
      gap: 12px;
      margin: 20px 0 30px 0;
      flex-wrap: wrap;
    }

    #custom-gallery-container .filter-tag {
      padding: 6px 18px;
      border-radius: 15px;
      background: #F0F9FF; 
      font-size: 0.85rem;
      cursor: pointer;
      border: 1px solid #e1f5fe;
      font-weight: 550;
      transition: all 0.3s ease;
      color: #003366;
    }

    #custom-gallery-container .filter-tag:hover { background: #E1F5FE; }

    #custom-gallery-container .filter-tag.active {
      background: #D4AF37;
      color: #ffffff;
      border-color: #D4AF37;
    }

    /* --- Mode 1: Masonry (For "All") --- */
    #custom-gallery-container .gallery-grid.masonry-mode {
      column-count: 3;
      column-gap: 15px;
      display: block; /* Overwrite flex */
    }

    #custom-gallery-container .masonry-mode .gallery-item {
      break-inside: avoid;
      display: inline-block;
      width: 100%;
      margin-bottom: 15px;
    }

    /* --- Mode 2: Horizontal (For Specific Categories) --- */
    #custom-gallery-container .gallery-grid.horizontal-mode {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      column-count: auto; /* Overwrite masonry */
    }

    #custom-gallery-container .horizontal-mode .gallery-item {
      flex: 0 0 auto; /* Do not grow, maintain aspect ratio */
      height: 250px;  /* Fixed height for horizontal alignment */
      width: auto;
    }

    #custom-gallery-container .horizontal-mode .gallery-item img {
      width: auto;    /* Width scales proportionally */
      height: 100%;
      object-fit: contain; /* Guarantee no cropping */
    }

    /* Common Item Styles */
    #custom-gallery-container .gallery-item {
      background-color: #f0f0f0;
      border-radius: 10px;
      overflow: hidden;
      position: relative;
      transition: transform 0.3s ease, opacity 0.3s ease;
    }

    #custom-gallery-container .gallery-item.hide { display: none !important; }

    #custom-gallery-container .gallery-item img {
      display: block;
      transition: transform 0.6s ease;
    }

    /* Responsive adjustments */
    @media (max-width: 900px) {
      #custom-gallery-container .gallery-grid.masonry-mode { column-count: 2; }
      #custom-gallery-container .horizontal-mode .gallery-item { height: 200px; }
    }
    @media (max-width: 600px) {
      #custom-gallery-container .gallery-grid.masonry-mode { column-count: 1; }
      #custom-gallery-container .horizontal-mode .gallery-item { height: 150px; }
    }

    /* Overlay Styles */
    #custom-gallery-container .gallery-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, rgba(0,0,0,0.4) 60%, transparent 100%);
      color: #fff;
      padding: 40px 15px 15px 15px;
      opacity: 0;
      transform: translateY(20px);
      transition: all 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
      pointer-events: none;
    }

    #custom-gallery-container .gallery-item:hover .gallery-overlay {
      opacity: 1;
      transform: translateY(0);
    }
    #custom-gallery-container .gallery-item:hover img { transform: scale(1.05); }

    .overlay-title { font-weight: 600; display: block; font-size: 0.9rem; }
    .overlay-desc { font-size: 0.75rem; opacity: 0.9; }
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

          // Switch layout mode based on filter
          if (selectedFilter === 'all') {
            grid.classList.remove('horizontal-mode');
            grid.classList.add('masonry-mode');
          } else {
            grid.classList.remove('masonry-mode');
            grid.classList.add('horizontal-mode');
          }

          // Filter logic
          items.forEach(item => {
            const category = item.getAttribute('data-category');
            if (selectedFilter === 'all' || category === selectedFilter) {
              item.classList.remove('hide');
              // Trigger a tiny reflow for opacity animation
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
