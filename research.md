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

## The Conquest

<div class="two-col">
  <div class="two-col-media">
    <img src="{{ '/assets/img/the-conquest.jpg' | relative_url }}" alt="The Conquest">
  </div>
  <div class="two-col-text">
    <p>
      When Aegon's Conquest of the Seven Kingdoms began, Visenya sailed with her siblings from Dragonstone. While Aegon began construction of the Aegonfort, Visenya subdued House Stokeworth by setting ablaze the roofs of Stokeworth. After the defeat of House Darklyn in Aegon's first test, Visenya claimed the riches of Duskendale, swelling the coffers of House Targaryen. Having conquered a dozen houses and secured the mouth of the Blackwater, Aegon was crowned king at the Aegonfort. Visenya, now queen, placed a Valyrian steel circlet on Aegon's head while their sister Rhaenys hailed him as the new King of All Westeros.
    </p>
  </div>
</div>

## Dance of the Dragons

<div class="two-col">
  <div class="two-col-media">
    <img src="{{ '/assets/img/dotd.png' | relative_url }}" alt="Dance of the Dragons">
  </div>
  <div class="two-col-text">
    <p>
      King Viserys I Targaryen had three children by his first queen, Aemma Arryn, but only one, Princess Rhaenyra, survived to adulthood. Lacking a son to succeed him, Viserys began to train Rhaenyra to be his heir. Young Rhaenyra was included in discussions of the affairs of state, and was allowed to participate in meetings of the small council. Many of the nobles took note, and Rhaenyra soon acquired a clique of adherents and supporters. After the passing of Queen Aemma in 105 AC, Viserys named Rhaenyra his heir and hundreds of lords and landed knights paid obeisance to her.
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
