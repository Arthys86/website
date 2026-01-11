---
layout: page
title: "Research"
subtitle: "research subtitle"
permalink: /research/
#full-width: true
---

<div id="journalCarousel" class="carousel slide journal-carousel" data-ride="carousel" data-interval="5000">
  <div class="carousel-inner">
    <div class="carousel-item active">
      <div class="cards-wrapper">
        <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="img-fluid cover-img" alt="Journal Cover"></div>
        <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="img-fluid cover-img" alt="Journal Cover"></div>
        <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="img-fluid cover-img" alt="Journal Cover"></div>
        <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="img-fluid cover-img" alt="Journal Cover"></div>
        <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="img-fluid cover-img" alt="Journal Cover"></div>
        <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="img-fluid cover-img" alt="Journal Cover"></div>
        <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="img-fluid cover-img" alt="Journal Cover"></div>
        <div class="cover-wrapper"><img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" class="img-fluid cover-img" alt="Journal Cover"></div>
      </div>
    </div>
  </div>

  <a class="carousel-control-prev" href="#journalCarousel" role="button" data-slide="prev">
    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
    <span class="sr-only">Previous</span>
  </a>
  <a class="carousel-control-next" href="#journalCarousel" role="button" data-slide="next">
    <span class="carousel-control-next-icon" aria-hidden="true"></span>
    <span class="sr-only">Next</span>
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
  const carousel = document.querySelector('#journalCarousel');
  const wrapper = carousel.querySelector('.cards-wrapper');
  const nextBtn = carousel.querySelector('.carousel-control-next');
  const prevBtn = carousel.querySelector('.carousel-control-prev');
  const items = carousel.querySelectorAll('.cover-wrapper');
  
  let currentIndex = 0;
  const itemsVisible = 5; 
  const maxIndex = items.length - itemsVisible; // For 8 items, maxIndex is 3

  function updateSlide() {
    // Each item takes 20% of the visible container width
    const slideAmount = currentIndex * -20; 
    wrapper.style.transform = `translateX(${slideAmount}%)`;
  }

  nextBtn.addEventListener('click', function(e) {
    e.preventDefault();
    e.stopPropagation(); // Stop Bootstrap's default slide behavior
    if (currentIndex < maxIndex) {
      currentIndex++;
    } else {
      currentIndex = 0; // Loop back to start
    }
    updateSlide();
  });

  prevBtn.addEventListener('click', function(e) {
    e.preventDefault();
    e.stopPropagation();
    if (currentIndex > 0) {
      currentIndex--;
    } else {
      currentIndex = maxIndex; // Loop to end
    }
    updateSlide();
  });
});
</script>
