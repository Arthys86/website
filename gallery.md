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

    /* 2. Layout Modes Configuration */

    /* [Centered Mode]: Zero crop, original ratio, row-based height */
    #custom-gallery-container .gallery-grid.mode-centered {
      display: flex;
      flex-direction: column; /* Stack rows vertically */
      gap: 15px;
      align-items: center; /* Center the rows */
    }

    #custom-gallery-container .mode-centered .gallery-row {
      display: flex;
      justify-content: center; /* Center images within the row */
      gap: 15px;
      width: 100%;
    }

    /* Set different heights for Row 1 and Row 2 */
    #custom-gallery-container .mode-centered .row-1 { height: 280px; }
    #custom-gallery-container .mode-centered .row-2 { height: 350px; }

    #custom-gallery-container .mode-centered .gallery-item {
      height: 100%; /* Fill the row height */
      flex: 0 0 auto; /* Do not stretch, maintain original width */
      position: relative;
    }

    #custom-gallery-container .mode-centered .gallery-item img {
      height: 100%;
      width: auto; /* Scale width proportionally to height */
      display: block;
      object-fit: contain; /* Guarantee no cropping */
    }

    /* [Column Mode]: Fixed 3-column grid */
    #custom-gallery-container .gallery-grid.mode-column {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 30px;
    }
    #custom-gallery-container .mode-column .gallery-item {
      flex: 0 1 calc(33.333% - 30px);
    }

    /* [Left Mode]: Left-aligned fixed height */
    #custom-gallery-container .gallery-grid.mode-left {
      display: flex;
      flex-wrap: wrap;
      justify-content: flex-start;
      gap: 15px;
    }
    #custom-gallery-container .mode-left .gallery-item {
      height: 250px;
    }

    /* Common Item Styles */
    #custom-gallery-container .gallery-item {
      border-radius: 10px;
      overflow: hidden;
      background: transparent !important;
      transition: transform 0.3s ease;
      position: relative;
    }

    /* 3. Restored Overlay Styling (Shows on hover) */
    #custom-gallery-container .gallery-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      /* Dark gradient at the bottom */
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

    .overlay-title { font-size: 0.95rem; font-weight: 600; display: block; }
    .overlay-desc { font-size: 0.75rem; opacity: 0.9; }

    #custom-gallery-container .gallery-item.hide { display: none !important; }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="centered">Centered</span>
    <span class="filter-tag" data-filter="left">Left</span>
    <span class="filter-tag" data-filter="column">Column</span>
    <span class="filter-tag" data-filter="masonry">Masonry</span>
  </div>

  <div class="gallery-grid mode-centered" id="gallery-grid">
    <div class="gallery-row row-1">
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
          <span class="overlay-desc">Archival Image</span>
        </div>
      </div>
      <div class="gallery-item">
        <img src="{{ site.baseurl }}/assets/img/darksister.jpeg" alt="Dark Sister">
        <div class="gallery-overlay">
          <span class="overlay-title">Dark Sister</span>
          <span class="overlay-desc">Ancient Artifact</span>
        </div>
      </div>
    </div>

    <div class="gallery-row row-2">
      <div class="gallery-item">
        <img src="{{ site.baseurl }}/assets/img/dotd.png" alt="Dance of the Dragons">
        <div class="gallery-overlay">
          <span class="overlay-title">Dance of the Dragons</span>
          <span class="overlay-desc">Historical Record</span>
        </div>
      </div>
      <div class="gallery-item">
        <img src="{{ site.baseurl }}/assets/img/placeholder-member.jpg" alt="Member">
        <div class="gallery-overlay">
          <span class="overlay-title">Team Member</span>
          <span class="overlay-desc">Researcher</span>
        </div>
      </div>
      <div class="gallery-item">
        <img src="{{ site.baseurl }}/assets/img/it.jpg" alt="Iron Throne">
        <div class="gallery-overlay">
          <span class="overlay-title">Iron Throne</span>
          <span class="overlay-desc">Relic Analysis</span>
        </div>
      </div>
    </div>
  </div>

  <script>
    /* Filter functionality */
    document.addEventListener("DOMContentLoaded", function() {
      const filters = document.querySelectorAll('#custom-gallery-container .filter-tag');
      const grid = document.getElementById('gallery-grid');

      filters.forEach(filter => {
        filter.addEventListener('click', function() {
          filters.forEach(f => f.classList.remove('active'));
          this.classList.add('active');
          const selectedFilter = this.getAttribute('data-filter');

          grid.className = 'gallery-grid mode-' + selectedFilter;
          // In actual use, more complex JS may be needed to handle row vs non-row structures
        });
      });
    });
  </script>
</div>
