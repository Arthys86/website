---
layout: page
title: "Research"
subtitle: "research subtitle"
permalink: /research/
---

<div id="journalCarousel" class="carousel slide journal-carousel">
  <div class="carousel-inner">
    <div class="cards-wrapper">
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="Journal 1"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="Journal 2"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="Journal 3"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="Journal 4"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="Journal 5"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="Journal 6"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="Journal 7"></div>
      <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="cover-img" alt="Journal 8"></div>
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

## Wearable haptic interfaces

<div class="two-col">
  <div class="two-col-media">
    <img src="{{ '/assets/img/the-conquest.jpg' | relative_url }}" alt="The Conquest">
  </div>
  <div class="two-col-text">
    <p>
      We develop haptic interfaces that help VR and AR users to feel the touch in the virtual world. Unlike commercial ones, our devices are no longer heavy or bulky, making users feel loaded or restricted. Instead, they can be made soft, thin, light-weighted, wearable and unobtrusive when using. Using wireless communication techs like Bluetooth Low Energy (BLE), stimulation could be triggered on anywhere of the hand by simply clicking a button on the mobile phone, or just be synchronized with the VR when collisions detected. In the future, we keep trying to make the interface more comfortable by using advanced materials and system integration strategies.
    </p>
  </div>
</div>

## Implantable bioelectronics

<div class="two-col">
  <div class="two-col-media">
    <img src="{{ '/assets/img/dotd.png' | relative_url }}" alt="Dance of the Dragons">
  </div>
  <div class="two-col-text">
    <p>
      We make efforts to develop advanced implantable bioelectronics for multi-purpose biomedical applications, such as electrophysiological signal monitoring (e.g. ECoG, EMG, EKG, etc.), electrostimulation for muscle rehabilitation, drug delivery, and neuromodulations (e.g. optogenetics, deep brain stimulations (DBS), vagus nerve stimulations (VNS), etc.). These implantables should be biocompatible that won't cause damage to the biological tissue, and will either be stable enough for long-term use or be transient that could be degraded by the body once it's not needed anymore, to avoid second-time surgery to take them out.
    </p>
  </div>
</div>

## Projects
- Project A
- Project B

<script>
document.addEventListener('DOMContentLoaded', function() {
  const wrapper = document.querySelector('.cards-wrapper');
  const nextBtn = document.querySelector('.carousel-control-next');
  const prevBtn = document.querySelector('.carousel-control-prev');
  const carousel = document.querySelector('#journalCarousel');
  
  let isTransitioning = false;
  const itemWidth = 20; // Each item takes 20% of the visible area
  let autoPlayTimer = null; 

  // --- Core Movement Logic ---

  function showNext() {
    if (isTransitioning) return;
    isTransitioning = true;
    wrapper.style.transition = 'transform 0.5s ease-in-out';
    wrapper.style.transform = `translateX(-${itemWidth}%)`;

    wrapper.addEventListener('transitionend', function handleEnd() {
      wrapper.style.transition = 'none';
      wrapper.appendChild(wrapper.firstElementChild); // Moves the first item to the end
      wrapper.style.transform = 'translateX(0)';
      setTimeout(() => { isTransitioning = false; }, 50);
      wrapper.removeEventListener('transitionend', handleEnd);
    });
  }

  function showPrev() {
    if (isTransitioning) return;
    isTransitioning = true;
    wrapper.style.transition = 'none';
    wrapper.prepend(wrapper.lastElementChild); // Moves the last item to the front
    wrapper.style.transform = `translateX(-${itemWidth}%)`;
    setTimeout(() => {
      wrapper.style.transition = 'transform 0.5s ease-in-out';
      wrapper.style.transform = 'translateX(0)';
    }, 10);
    wrapper.addEventListener('transitionend', () => { isTransitioning = false; }, {once: true});
  }

  // --- Standardized Timer Management (The Fix for your issue) ---

  function stopAutoPlay() {
    if (autoPlayTimer) {
      clearInterval(autoPlayTimer);
      autoPlayTimer = null;
    }
  }

  function startAutoPlay() {
    stopAutoPlay(); // Kill any existing timer first to prevent stacking
    autoPlayTimer = setInterval(showNext, 3000); // Set to 5 seconds
  }

  // Manual Controls
  nextBtn.addEventListener('click', (e) => { 
    e.preventDefault(); 
    showNext(); 
    startAutoPlay(); // Restart the 5s countdown from zero
  });

  prevBtn.addEventListener('click', (e) => { 
    e.preventDefault(); 
    showPrev(); 
    startAutoPlay(); // Restart the 5s countdown from zero
  });

  // Hover Behavior: Pauses on mouse over, resumes on mouse out
  carousel.addEventListener('mouseenter', stopAutoPlay);
  carousel.addEventListener('mouseleave', startAutoPlay);

  // Initial Boot
  startAutoPlay();
});
</script>
