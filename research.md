---
layout: page
title: "Research"
subtitle: "research subtitle"
permalink: /research/
---

<div id="journalCarousel" class="carousel slide journal-carousel">
  <div class="carousel-inner">
    <div class="cards-wrapper">
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="1"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="2"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="3"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="4"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="5"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="6"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="7"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="8"></div>
    </div>
  </div>

  <a class="carousel-control-prev" href="javascript:void(0)" role="button">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
  </a>
  <a class="carousel-control-next" href="javascript:void(0)" role="button">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
  </a>
</div>

<hr>

<script>
document.addEventListener('DOMContentLoaded', function() {
  const wrapper = document.querySelector('.cards-wrapper');
  const nextBtn = document.querySelector('.carousel-control-next');
  const prevBtn = document.querySelector('.carousel-control-prev');
  const carousel = document.querySelector('#journalCarousel');
  
  let isTransitioning = false;
  const itemWidth = 20; // 20% for each of 5 visible items

  function showNext() {
    if (isTransitioning) return;
    isTransitioning = true;

    // 1. Move the wrapper to the left with animation
    wrapper.style.transition = 'transform 0.5s ease-in-out';
    wrapper.style.transform = `translateX(-${itemWidth}%)`;

    // 2. After animation, move the first element to the end and reset position
    wrapper.addEventListener('transitionend', function handleEnd() {
      wrapper.style.transition = 'none';
      wrapper.appendChild(wrapper.firstElementChild); // Move first to last
      wrapper.style.transform = 'translateX(0)';
      
      // Use a tiny timeout to ensure the transition:none is applied before allowing next slide
      setTimeout(() => { isTransitioning = false; }, 50);
      wrapper.removeEventListener('transitionend', handleEnd);
    });
  }

  function showPrev() {
    if (isTransitioning) return;
    isTransitioning = true;

    // 1. Instantly move the last element to the front
    wrapper.style.transition = 'none';
    wrapper.prepend(wrapper.lastElementChild);
    // 2. Offset the wrapper to the left to compensate for the new first element
    wrapper.style.transform = `translateX(-${itemWidth}%)`;

    // 3. Animate back to 0 position
    setTimeout(() => {
      wrapper.style.transition = 'transform 0.5s ease-in-out';
      wrapper.style.transform = 'translateX(0)';
    }, 10);

    wrapper.addEventListener('transitionend', () => {
      isTransitioning = false;
    }, {once: true});
  }

  // Click events
  nextBtn.addEventListener('click', (e) => { 
    e.preventDefault(); 
    showNext(); 
    resetAutoPlay(); 
  });
  
  prevBtn.addEventListener('click', (e) => { 
    e.preventDefault(); 
    showPrev(); 
    resetAutoPlay(); 
  });

  // AutoPlay
  let autoPlayTimer = setInterval(showNext, 5000);
  
  function resetAutoPlay() {
    clearInterval(autoPlayTimer);
    autoPlayTimer = setInterval(showNext, 5000);
  }

  carousel.addEventListener('mouseenter', () => clearInterval(autoPlayTimer));
  carousel.addEventListener('mouseleave', startAutoPlay);
  
  function startAutoPlay() {
    clearInterval(autoPlayTimer);
    autoPlayTimer = setInterval(showNext, 5000);
  }
});
</script>
