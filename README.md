# HeroSliderJS
Vanilla JS Hero Slider Logo 


```HTML
<style>

    .lp-slider-container {
      width: 100%;
      overflow: hidden;
      padding: 40px 0;
      display: flex;
      justify-content: center;
      position: relative;
    }

    .lp-slider-wrapper {
      width: 1120px;
      overflow: hidden;
      position: relative;
    }

    .lp-slider-track {
      display: flex;
      transition: transform 0.5s ease-in-out;
    }

    .lp-slider-slide {
      width: 200px;
      height: 300px;
      margin: 0 10px;
      background-color: #555;
      color: #fff;
      font-size: 24px;
      display: flex;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      border-radius: 10px;
      position: relative;
    }

    .lp-slider-slide:first-child,
    .lp-slider-slide:last-child {
      opacity: 0.5;
    }

    .lp-slider-arrow {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      font-size: 32px;
      color: white;
      background: rgba(0, 0, 0, 0.6);
      border-radius: 50%;
      width: 40px;
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      z-index: 10;
      user-select: none;
    }

    /* Fixed arrow positions on second and fourth slides */
    .lp-slider-left-arrow {
      left: calc(220px * 1 + 10px);
    }

    .lp-slider-right-arrow {
      left: calc(220px * 3 + 10px);
    }
  </style>

  <div class="lp-slider-container">
    <div class="lp-slider-wrapper">
      <div class="lp-slider-track" id="lp_slider_track">
        <div class="lp-slider-slide">1</div>
        <div class="lp-slider-slide">2</div>
        <div class="lp-slider-slide">3</div>
        <div class="lp-slider-slide">4</div>
        <div class="lp-slider-slide">5</div>
      </div>

      <!-- Fixed arrows -->
      <div class="lp-slider-arrow lp-slider-left-arrow" onclick="lp_slider_slideLeft()">&#9664;</div>
      <div class="lp-slider-arrow lp-slider-right-arrow" onclick="lp_slider_slideRight()">&#9654;</div>
    </div>
  </div>

  <script>
    const lp_slider_track = document.getElementById('lp_slider_track');

    function lp_slider_slideLeft() {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      const firstSlide = slides[0];

      lp_slider_track.style.transition = 'transform 0.5s ease-in-out';
      lp_slider_track.style.transform = `translateX(-220px)`;

      setTimeout(() => {
        lp_slider_track.appendChild(firstSlide);
        lp_slider_track.style.transition = 'none';
        lp_slider_track.style.transform = 'translateX(0)';
      }, 500);
    }

    function lp_slider_slideRight() {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      const lastSlide = slides[slides.length - 1];

      lp_slider_track.style.transition = 'none';
      lp_slider_track.insertBefore(lastSlide, slides[0]);
      lp_slider_track.style.transform = 'translateX(-220px)';

      requestAnimationFrame(() => {
        lp_slider_track.style.transition = 'transform 0.5s ease-in-out';
        lp_slider_track.style.transform = 'translateX(0)';
      });
    }
  </script>

```
