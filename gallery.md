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

    /* Unselected State */
    #custom-gallery-container .filter-tag {
      padding: 6px 18px;
      border-radius: 15px;
      background: #F0F9FF; /* Very light blue as requested */
      font-size: 0.85rem;
      cursor: pointer;
      border: 1px solid #e1f5fe; /* Light border to match */
      font-weight: 550;
      transition: all 0.3s ease;
      color: #003366; /* UST Deep Blue */
    }

    /* Hover State */
    #custom-gallery-container .filter-tag:hover {
      background: #E1F5FE; /* Your chosen blue-light color */
    }

    /* Selected (Active) State: Remains Gold as per previous design */
    #custom-gallery-container .filter-tag.active {
      background: #D4AF37; /* Light Gold */
      color: #ffffff;      /* White text */
      border-color: #D4AF37;
    }

    /* Masonry Grid Layout */
    #custom-gallery-container .gallery-columns {
      column-count: 3;
      column-gap: 15px;
    }

    @media (max-width: 900px) { #custom-gallery-container .gallery-columns { column-count: 2; } }
    @media (max-width: 600px) { #custom-gallery-container .gallery-columns { column-count: 1; } }

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
      transition: transform 0.6s ease;
    }

    /* Bottom Gradient Overlay */
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

    #custom-gallery-container .overlay-title {
      font-size: 1rem;
      font-weight: 600;
      display: block;
      margin-bottom: 2px;
      text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
    }

    #custom-gallery-container .overlay-desc {
      font-size: 0.8rem;
      opacity: 0.9;
      line-height: 1.3;
      display: block;
    }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">All</span>
    <span class="filter-tag" data-filter="history">History</span>
    <span class="filter-tag" data-filter="characters">Characters</span>
    <span class="filter-tag" data-filter="artifacts">Artifacts</span>
  </div>

  <div class="gallery-columns" id="gallery-grid">
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

      filters.forEach(filter => {
        filter.addEventListener('click', function() {
          filters.forEach(f => f.classList.remove('active'));
          this.classList.add('active');
          const selectedFilter = this.getAttribute('data-filter');
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
