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
      background: #f8f9fa;
      font-size: 0.85rem;
      cursor: pointer;
      border: 1px solid #eee;
      font-weight: 550;
      transition: all 0.2s ease;
      color: #666;
    }

    #custom-gallery-container .filter-tag:hover { background: #e9ecef; }

    #custom-gallery-container .filter-tag.active {
      background: #333;
      color: #fff;
      border-color: #333;
    }

    /* Masonry Grid (Respects aspect ratio) */
    #custom-gallery-container .gallery-columns {
      column-count: 3;
      column-gap: 15px;
    }

    @media (max-width: 800px) { #custom-gallery-container .gallery-columns { column-count: 2; } }
    @media (max-width: 500px) { #custom-gallery-container .gallery-columns { column-count: 1; } }

    /* Gallery Item Card */
    #custom-gallery-container .gallery-item {
      display: inline-block;
      width: 100%;
      margin-bottom: 15px;
      background-color: #f0f0f0;
      border-radius: 10px;
      overflow: hidden;
      position: relative;
      transition: transform 0.3s ease;
    }

    #custom-gallery-container .gallery-item.hide { display: none; }

    #custom-gallery-container .gallery-item img {
      width: 100%;
      height: auto;
      display: block;
      transition: transform 0.5s ease;
    }

    /* Improved Overlay: Bottom Gradient Information Bar */
    #custom-gallery-container .gallery-overlay {
      position: absolute;
      bottom: 0;
      left: 0;
      right: 0;
      /* Gradient background for better legibility without blocking the whole image */
      background: linear-gradient(to top, rgba(0,0,0,0.8) 0%, rgba(0,0,0,0.4) 60%, transparent 100%);
      color: #fff;
      padding: 40px 15px 15px 15px; /* Extra top padding for the gradient blend */
      opacity: 0;
      transform: translateY(10px);
      transition: all 0.3s ease;
      text-align: left;
    }

    #custom-gallery-container .gallery-item:hover .gallery-overlay {
      opacity: 1;
      transform: translateY(0);
    }

    #custom-gallery-container .gallery-item:hover img {
      transform: scale(1.04);
    }

    #custom-gallery-container .overlay-title {
      font-size: 1rem;
      font-weight: 600;
      display: block;
      margin-bottom: 4px;
    }

    #custom-gallery-container .overlay-desc {
      font-size: 0.8rem;
      opacity: 0.9;
      line-height: 1.2;
    }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">All</span>
    <span class="filter-tag" data-filter="research">History</span>
    <span class="filter-tag" data-filter="team">Characters</span>
  </div>

  <div class="gallery-columns">
    
    <div class="gallery-item" data-category="research">
      <img src="{{ site.baseurl }}/assets/img/dotd.png" alt="Dance of the Dragons">
      <div class="gallery-overlay">
        <span class="overlay-title">Dance of the Dragons</span>
        <span class="overlay-desc">Dance of the Dragons</span>
      </div>
    </div>

    <div class="gallery-item" data-category="team">
      <img src="{{ site.baseurl }}/assets/img/placeholder-member.jpg" alt="Daemon Targaryen">
      <div class="gallery-overlay">
        <span class="overlay-title">Daemon Targaryen</span>
        <span class="overlay-desc">The Rogue Prince, Commander of the City Watch</span>
      </div>
    </div>

    <div class="gallery-item" data-category="research">
      <img src="{{ site.baseurl }}/assets/img/the-conquest.jpg" alt="The Conquest">
      <div class="gallery-overlay">
        <span class="overlay-title">The Conquest</span>
        <span class="overlay-desc">Visenya Targaryen and Vhagar</span>
      </div>
    </div>

  </div>

  <script>
    document.addEventListener("DOMContentLoaded", function() {
      const filters = document.querySelectorAll('#custom-gallery-container .filter-tag');
      const items = document.querySelectorAll('#custom-gallery-container .gallery-item');

      filters.forEach(filter => {
        filter.addEventListener('click', function() {
          filters.forEach(f => f.classList.remove('active'));
          this.classList.add('active');

          const selectedFilter = this.getAttribute('data-filter');

          items.forEach(item => {
            const category = item.getAttribute('data-category');
            if (selectedFilter === 'all' || category === selectedFilter) {
              item.classList.remove('hide');
            } else {
              item.classList.add('hide');
            }
          });
        });
      });
    });
  </script>
</div>
