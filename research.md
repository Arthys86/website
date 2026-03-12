---
layout: page
title: "Research"
subtitle: "research subtitle"
permalink: /research/
---

<style>
  /* --------- Section titles --------- */
  .research-section-title {
    margin: 2.2rem 0 1.2rem;
    font-size: 1.8rem;
    font-weight: 700;
    line-height: 1.3;
  }

  /* --------- Two-column layout --------- */
  .two-col {
    display: flex;
    gap: 2rem;
    align-items: flex-start;
    margin-bottom: 2.5rem;
  }

  .two-col-media {
    flex: 0 0 42%;
  }

  .two-col-text {
    flex: 1 1 auto;
  }

  .two-col-text p {
    margin-top: 0;
  }

  .two-col-media img {
    width: 100%;
    height: auto;
    display: block;
    border-radius: 8px;
  }

  /* --------- Manual carousel inside two-col --------- */
  .research-carousel {
    position: relative;
    overflow: hidden;
    width: 100%;
    border-radius: 8px;
  }

  .research-carousel-track {
    display: flex;
    transition: transform 0.5s ease-in-out;
    will-change: transform;
  }

  .research-carousel-slide {
    min-width: 100%;
    flex: 0 0 100%;
  }

  .research-carousel-slide img {
    width: 100%;
    height: auto;
    display: block;
    border-radius: 8px;
  }

  .research-carousel-prev,
  .research-carousel-next {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    z-index: 2;
    width: 2.6rem;
    height: 2.6rem;
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    cursor: pointer;
    background: rgba(255, 255, 255, 0.72);
    border-radius: 50%;
    transition: background 0.2s ease;
  }

  .research-carousel-prev:hover,
  .research-carousel-next:hover {
    background: rgba(255, 255, 255, 0.9);
  }

  .research-carousel-prev {
    left: 0.7rem;
  }

  .research-carousel-next {
    right: 0.7rem;
  }

  /* Use the same Bootstrap arrow icons style */
  .research-carousel-prev .carousel-control-prev-icon,
  .research-carousel-next .carousel-control-next-icon {
    filter: invert(25%);
  }

  /* --------- Responsive --------- */
  @media (max-width: 768px) {
    .two-col {
      flex-direction: column;
    }

    .two-col-media,
    .two-col-text {
      flex: 1 1 100%;
      width: 100%;
    }
  }
</style>

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

<h2 class="research-section-title">Wearable haptic interfaces</h2>

<div class="two-col">
  <div class="two-col-media">
    <div class="research-carousel" data-carousel="wearable-haptics">
      <div class="research-carousel-track">
        <div class="research-carousel-slide">
          <img src="{{ '/assets/img/the-conquest.jpg' | relative_url }}" alt="Wearable haptic interfaces 1">
        </div>
        <div class="research-carousel-slide">
          <img src="{{ '/assets/img/darksister.jpeg' | relative_url }}" alt="Wearable haptic interfaces 2">
        </div>
        <div class="research-carousel-slide">
          <img src="{{ '/assets/img/dotd.png' | relative_url }}" alt="Wearable haptic interfaces 3">
        </div>
      </div>

      <a class="research-carousel-prev" href="javascript:void(0)" aria-label="Previous image">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
      </a>
      <a class="research-carousel-next" href="javascript:void(0)" aria-label="Next image">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
      </a>
    </div>
  </div>

  <div class="two-col-text">
    <p>
      We develop haptic interfaces that help VR and AR users to feel touch in the virtual world.
      Unlike commercial ones, our devices are no longer heavy or bulky, making users feel loaded
      or restricted. Instead, they can be soft, thin, lightweight, wearable and unobtrusive.
      Using wireless communication technologies such as Bluetooth Low Energy (BLE), stimulation
      can be triggered anywhere on the hand by simply clicking a button on the mobile phone,
      or synchronized with the VR system when collisions are detected. In the future, we will
      continue making the interface more comfortable through advanced materials and system
      integration strategies.
    </p>
  </div>
</div>

<h2 class="research-section-title">Implantable bioelectronics</h2>

<div class="two-col">
  <div class="two-col-media">
    <img src="{{ '/assets/img/dotd.png' | relative_url }}" alt="Implantable bioelectronics">
  </div>
  <div class="two-col-text">
    <p>
      We make efforts to develop advanced implantable bioelectronics for multi-purpose biomedical
      applications, such as electrophysiological signal monitoring (e.g. ECoG, EMG, EKG, etc.),
      electrostimulation for muscle rehabilitation, drug delivery, and neuromodulation
      (e.g. optogenetics, deep brain stimulation (DBS), vagus nerve stimulation (VNS), etc.).
      These implantables should be biocompatible and should not damage biological tissue.
      They should either be stable enough for long-term use or transient enough to degrade
      in the body once no longer needed, avoiding secondary removal surgery.
    </p>
  </div>
</div>

<h2 class="research-section-title">Advanced manufacturing: soft, permeable 3D electronic system</h2>

<div class="two-col">
  <div class="two-col-media">
    <img src="{{ '/assets/img/the-conquest.jpg' | relative_url }}" alt="Advanced manufacturing: soft, permeable 3D electronic system">
  </div>
  <div class="two-col-text">
    <p>
      Most stretchable electronic systems have low-density integration and are wired with external
      printed circuit boards, which limits functionality, deteriorates user experience and impedes
      long-term usability. Here we report an intrinsically permeable, three-dimensional integrated
      electronic skin. The system combines high-density inorganic electronic components with organic
      stretchable fibrous substrates using three-dimensional patterned, multilayered liquid metal
      circuits and stretchable hybrid liquid metal solder. The electronic skin exhibits high softness,
      durability, fabric-like permeability to air and moisture, and sufficient biocompatibility for
      on-skin attachment for a week.
    </p>
  </div>
</div>

<h2 class="research-section-title">Projects</h2>
<ul>
  <li>Project A</li>
  <li>Project B</li>
</ul>

<script>
document.addEventListener('DOMContentLoaded', function() {
  /* ---------- Top journal carousel: keep autoplay ---------- */
  const wrapper = document.querySelector('.cards-wrapper');
  const nextBtn = document.querySelector('#journalCarousel .carousel-control-next');
  const prevBtn = document.querySelector('#journalCarousel .carousel-control-prev');
  const carousel = document.querySelector('#journalCarousel');

  let isTransitioning = false;
  const itemWidth = 20;
  let autoPlayTimer = null;

  function showNext() {
    if (isTransitioning) return;
    isTransitioning = true;
    wrapper.style.transition = 'transform 0.5s ease-in-out';
    wrapper.style.transform = `translateX(-${itemWidth}%)`;

    wrapper.addEventListener('transitionend', function handleEnd() {
      wrapper.style.transition = 'none';
      wrapper.appendChild(wrapper.firstElementChild);
      wrapper.style.transform = 'translateX(0)';
      setTimeout(() => { isTransitioning = false; }, 50);
      wrapper.removeEventListener('transitionend', handleEnd);
    });
  }

  function showPrev() {
    if (isTransitioning) return;
    isTransitioning = true;
    wrapper.style.transition = 'none';
    wrapper.prepend(wrapper.lastElementChild);
    wrapper.style.transform = `translateX(-${itemWidth}%)`;
    setTimeout(() => {
      wrapper.style.transition = 'transform 0.5s ease-in-out';
      wrapper.style.transform = 'translateX(0)';
    }, 10);
    wrapper.addEventListener('transitionend', () => {
      isTransitioning = false;
    }, { once: true });
  }

  function stopAutoPlay() {
    if (autoPlayTimer) {
      clearInterval(autoPlayTimer);
      autoPlayTimer = null;
    }
  }

  function startAutoPlay() {
    stopAutoPlay();
    autoPlayTimer = setInterval(showNext, 3000);
  }

  nextBtn.addEventListener('click', (e) => {
    e.preventDefault();
    showNext();
    startAutoPlay();
  });

  prevBtn.addEventListener('click', (e) => {
    e.preventDefault();
    showPrev();
    startAutoPlay();
  });

  carousel.addEventListener('mouseenter', stopAutoPlay);
  carousel.addEventListener('mouseleave', startAutoPlay);

  startAutoPlay();

  /* ---------- Manual research image carousel: no autoplay ---------- */
  document.querySelectorAll('.research-carousel').forEach(function(carouselEl) {
    const track = carouselEl.querySelector('.research-carousel-track');
    const slides = carouselEl.querySelectorAll('.research-carousel-slide');
    const prev = carouselEl.querySelector('.research-carousel-prev');
    const next = carouselEl.querySelector('.research-carousel-next');

    let index = 0;
    const total = slides.length;

    function updateCarousel() {
      track.style.transform = `translateX(-${index * 100}%)`;
    }

    next.addEventListener('click', function(e) {
      e.preventDefault();
      index = (index + 1) % total;
      updateCarousel();
    });

    prev.addEventListener('click', function(e) {
      e.preventDefault();
      index = (index - 1 + total) % total;
      updateCarousel();
    });
  });
});
</script>
