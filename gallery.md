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

    /* 2. MODE: Centered - ONLY PART MODIFIED */
    /* Ensuring all images in a row have identical physical height without cropping */
    #custom-gallery-container .gallery-grid.mode-centered {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 15px;
    }
    
    #custom-gallery-container .mode-centered .gallery-item {
      height: 300px; /* Base row height for all items in this mode */
      flex: 0 0 auto;
      display: flex;
    }

    #custom-gallery-container .mode-centered .gallery-item img {
      height: 100%;  /* Force image to fill the 300px container height */
      width: auto;   /* Scale width proportionally - No Crop */
      display: block;
      object-fit: contain;
    }

    /* Special rule to separate row 1 and row 2 if desired, 
       or let them flow naturally while maintaining height consistency */
    #custom-gallery-container .mode-centered .gallery-item:nth-child(3)::after {
      content: "";
      flex-basis: 100%;
      width: 0;
      height: 0;
    }

    /* 3. MODE: Left - NO CHANGES */
    #custom-gallery-container .gallery-grid.mode-left {
      display: flex;
      flex-wrap: wrap;
      justify-content: flex-start;
      gap: 15px;
    }
    #custom-gallery-container .mode-left .gallery-item {
      height: 250px;
      flex: 0 0 auto;
    }
    #custom-gallery-container .mode-left .gallery-item img {
      height: 100%;
      width: auto;
    }

    /* 4. MODE: Column - NO CHANGES (Strictly original 3-column logic) */
    #custom-gallery-container .gallery-grid.mode-column {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center; 
      gap: 30px;
    }
    #custom-gallery-container .mode-column .gallery-item {
      flex: 0 1 calc(33.333% - 30px);
    }
    #custom-gallery-container .mode-column .gallery-item img {
      width: 100%;
      height: auto;
    }

    /* 5. MODE: Masonry - NO CHANGES */
    #custom-gallery-container .gallery-grid.mode-masonry {
      display: block;
      column-count: 3;
      column-gap: 20px;
    }
    #custom-gallery-container .mode-masonry .gallery-item {
      display: block;
      width: 100%;
      margin-bottom: 20px;
    }

    /* 6. Shared Components (Overlay/Hover) - NO CHANGES */
    #custom-gallery-container .gallery-item {
      position: relative;
      border-radius: 10px;
      overflow: hidden;
      background: transparent;
      transition: transform 0.3s ease;
    }

    #custom-gallery-container .gallery-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      background: linear-gradient(to top, rgba(0,0,0,0.85) 0%, rgba(0,0,0,0) 100%);
      color: #fff;
      padding: 40px 15px 15px 15px;
      opacity: 0;
      transform: translateY(10px);
      transition: all 0.3s ease;
      pointer-events: none;
      z-index: 2;
    }
    
    #custom-gallery-container .gallery-item:hover .gallery-overlay { 
      opacity: 1; 
      transform: translateY(0); 
    }
    
    #custom-gallery-container .gallery-item:hover img { 
      transform: scale(1.03); 
    }

    .overlay-title { font-size: 0.95rem; font-weight: 600; display: block; margin-bottom: 4px; }
    .overlay-desc { font-size: 0.75rem; opacity: 0.9; line-height: 1.2; }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="centered">Centered</span>
    <span class="filter-tag" data-filter="left">Left</span>
    <span class="filter-tag" data-filter="column">Column</span>
    <span class="filter-tag" data-filter="masonry">Masonry</span>
  </div>

  <div class="gallery-grid mode-centered" id="gallery-grid">
    <div class="gallery-item">
      <img src="{{ site.baseurl }}/assets/img/pi.jpg" alt="Who">
      <div class="gallery-overlay">
        <span class="overlay-title">Who</span>
        <span class="overlay-desc">I don't know</span>
      </div>
    </div>

    <div class="gallery-item">
      <img src="{{ site.baseurl }}/assets/img/the-conquest.jpg" alt="The Conquest">
      <div class="gallery-overlay">
        <span class="overlay-title">The Conquest</span>
        <span class="overlay-desc">Visenya Targaryen and Vhagar</span>
      </div>
    </div>

    <div class="gallery-item">
      <img src="{{ site.baseurl }}/assets/img/darksister.jpeg" alt="Dark Sister">
      <div class="gallery-overlay">
        <span class="overlay-title">Dark Sister</span>
        <span class="overlay-desc">a longsword of Valyrian steel</span>
      </div>
    </div>

    <div class="gallery-item">
      <img src="{{ site.baseurl }}/assets/img/dotd.png" alt="Dance of the Dragons">
      <div class="gallery-overlay">
        <span class="overlay-title">Dance of the Dragons</span>
        <span class="overlay-desc">The Dance over Shipbreaker Bay</span>
      </div>
    </div>

    <div class="gallery-item">
      <img src="{{ site.baseurl }}/assets/img/placeholder-member.jpg" alt="Daemon Targaryen">
      <div class="gallery-overlay">
        <span class="overlay-title">Daemon Targaryen</span>
        <span class="overlay-desc">The Rogue Prince, Commander of the City Watch</span>
      </div>
    </div>

    <div class="gallery-item">
      <img src="{{ site.baseurl }}/assets/img/it.jpg" alt="Iron Throne">
      <div class="gallery-overlay">
        <span class="overlay-title">Iron Throne</span>
        <span class="overlay-desc">The throne of the monarchs of the Seven Kingdoms</span>
      </div>
    </div>
  </div>

  <script>
    document.addEventListener("DOMContentLoaded", function() {
      const filters = document.querySelectorAll('#custom-gallery-container .filter-tag');
      const grid = document.getElementById('gallery-grid');

      filters.forEach(filter => {
        filter.addEventListener('click', function() {
          filters.forEach(f => f.classList.remove('active'));
          this.classList.add('active');
          const selectedFilter = this.getAttribute('data-filter');
          grid.className = 'gallery-grid mode-' + selectedFilter;
        });
      });
    });
  </script>
</div>
