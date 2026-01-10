---
layout: page
title: "Gallery"
subtitle: "Gallery subtitle"
permalink: /gallery/
---

<div id="custom-gallery-container">
  <style>
    /* Filter Tags Container */
    #custom-gallery-container .gallery-filters {
      display: flex;
      gap: 12px;
      margin: 20px 0 30px 0;
      flex-wrap: wrap;
    }

    /* Individual Filter Tag */
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

    #custom-gallery-container .filter-tag:hover {
      background: #e9ecef;
    }

    /* Active Tag Style */
    #custom-gallery-container .filter-tag.active {
      background: #333;
      color: #fff;
      border-color: #333;
    }

    /* Masonry Layout Container */
    #custom-gallery-container .gallery-columns {
      column-count: 3;
      column-gap: 15px;
      min-height: 400px;
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
      transition: transform 0.3s ease, opacity 0.3s ease;
    }

    /* Hidden state for filtering */
    #custom-gallery-container .gallery-item.hide {
      display: none;
    }

    #custom-gallery-container .gallery-item img {
      width: 100%;
      height: auto;
      display: block;
      transition: transform 0.4s ease;
    }

    /* Hover Overlay */
    #custom-gallery-container .gallery-overlay {
      position: absolute;
      inset: 0;
      background: rgba(0,0,0,0.6);
      color: #fff;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      opacity: 0;
      transition: opacity 0.3s ease;
      padding: 20px;
      text-align: center;
    }

    #custom-gallery-container .gallery-item:hover .gallery-overlay {
      opacity: 1;
    }

    #custom-gallery-container .gallery-item:hover img {
      transform: scale(1.05);
    }
  </style>

  <div class="gallery-filters">
    <span class="filter-tag active" data-filter="all">All</span>
    <span class="filter-tag" data-filter="research">Research</span>
    <span class="filter-tag" data-filter="life">Life</span>
    <span class="filter-tag" data-filter="team">Team</span>
  </div>

  <div class="gallery-columns" id="gallery-grid">
    
    <div class="gallery-item" data-category="research">
      <img src="{{ site.baseurl }}/assets/img/the-conquest.jpg" alt="Research Work">
      <div class="gallery-overlay">
        <strong>Research Highlight</strong>
        <p style="font-size:0.8rem;">Experimental setup for soft electronics.</p>
      </div>
    </div>

    <div class="gallery-item" data-category="team">
      <img src="{{ site.baseurl }}/assets/img/placeholder-member.jpg" alt="Member Photo">
      <div class="gallery-overlay">
        <strong>Our Team</strong>
        <p style="font-size:0.8rem;">Core members and contributors.</p>
      </div>
    </div>

    <div class="gallery-item" data-category="research">
      <img src="{{ site.baseurl }}/assets/img/dotd.png" alt="Device Detail">
      <div class="gallery-overlay">
        <strong>Device Fabrication</strong>
        <p style="font-size:0.8rem;">Nanoscale structural analysis results.</p>
      </div>
    </div>

    <div class="gallery-item" data-category="life">
      <img src="{{ site.baseurl }}/assets/img/the-conquest.jpg" alt="Social Event">
      <div class="gallery-overlay">
        <strong>Lab Life</strong>
        <p style="font-size:0.8rem;">Moments outside the cleanroom.</p>
      </div>
    </div>

    <div class="gallery-item" data-category="team">
      <img src="{{ site.baseurl }}/assets/img/placeholder-member.jpg" alt="Seminar">
      <div class="gallery-overlay">
        <strong>Seminar Session</strong>
        <p style="font-size:0.8rem;">Weekly technical exchange and discussion.</p>
      </div>
    </div>

  </div>

  <script>
    document.addEventListener("DOMContentLoaded", function() {
      const filters = document.querySelectorAll('#custom-gallery-container .filter-tag');
      const items = document.querySelectorAll('#custom-gallery-container .gallery-item');

      filters.forEach(filter => {
        filter.addEventListener('click', function() {
          // Update active class for buttons
          filters.forEach(f => f.classList.remove('active'));
          this.classList.add('active');

          const selectedFilter = this.getAttribute('data-filter');

          // Filter gallery items
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
