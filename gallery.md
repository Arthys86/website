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

    #custom-gallery-container .filter-tag:hover {
      background: #E1F5FE;
    }

    #custom-gallery-container .filter-tag.active {
      background: #D4AF37;
      color: #ffffff;
      border-color: #D4AF37;
    }

    /* Horizontal Layout: Flexbox */
    #custom-gallery-container .gallery-columns {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
    }

    /* Consistent Height & Proportional Scaling */
    #custom-gallery-container .gallery-item {
      flex: 1 0 auto; /* Allow items to grow to fill space */
      height: 250px;  /* Fixed height for all images in a row */
      min-width: 150px;
      background-color: #f0f0f0;
      border-radius: 10px;
      overflow: hidden;
      position: relative;
      transition: transform 0.3s ease;
    }

    #custom-gallery-container .gallery-item.hide { display: none; }

    #custom-gallery-container .gallery-item img {
      width: auto;
      min-width: 100%;
      height: 100%;
      object-fit: cover; /* Ensures image fills the height-consistent box without distortion */
      display: block;
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
    }

    /* Responsive adjustment for mobile */
    @media (max-width: 600px) {
      #custom-gallery-container .gallery-item {
        height: 180px; /* Shorter height for smaller screens */
        flex: 1 0 100%; /* Full width on mobile if desired */
      }
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
              item.style.display = "inline-block"; // Ensure it shows for flex
              item.style.opacity = "0";
              setTimeout(() => { item.style.opacity = "1"; }, 10);
            } else {
              item.classList.add('hide');
              item.style.display = "none";
            }
          });
        });
      });
    });
  </script>
</div>
