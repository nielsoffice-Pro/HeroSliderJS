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


```HTML

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>LP Slider</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: sans-serif;
      background: #111;
    }

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
      transition: opacity 0.3s ease;
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

    .lp-slider-left-arrow {
      left: calc(220px * 1 + 10px);
    }

    .lp-slider-right-arrow {
      left: calc(220px * 3 + 10px);
    }

    .lp-slider-dim {
      opacity: 0.3 !important;
    }
  </style>
</head>
<body>

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
      <div
        class="lp-slider-arrow lp-slider-left-arrow"
        id="lp_slider_left_arrow"
        onmouseover="lp_slider_dimColumn(1)"
        onmouseout="lp_slider_resetDim(1)"
        onclick="lp_slider_slideLeft()"
      >&#9664;</div>

      <div
        class="lp-slider-arrow lp-slider-right-arrow"
        id="lp_slider_right_arrow"
        onmouseover="lp_slider_dimColumn(3)"
        onmouseout="lp_slider_resetDim(3)"
        onclick="lp_slider_slideRight()"
      >&#9654;</div>
    </div>
  </div>

  <script>
    const lp_slider_track = document.getElementById('lp_slider_track');
  
    function lp_slider_slideLeft() {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      const firstSlide = slides[0];
  
      lp_slider_clearDim(); // <- clear opacity before sliding
  
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
  
      lp_slider_clearDim(); // <- clear opacity before sliding
  
      lp_slider_track.style.transition = 'none';
      lp_slider_track.insertBefore(lastSlide, slides[0]);
      lp_slider_track.style.transform = 'translateX(-220px)';
  
      requestAnimationFrame(() => {
        lp_slider_track.style.transition = 'transform 0.5s ease-in-out';
        lp_slider_track.style.transform = 'translateX(0)';
      });
    }
  
    function lp_slider_dimColumn(index) {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      if (slides[index]) {
        slides[index].classList.add('lp-slider-dim');
      }
    }
  
    function lp_slider_resetDim(index) {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      if (slides[index]) {
        slides[index].classList.remove('lp-slider-dim');
      }
    }
  
    function lp_slider_clearDim() {
      const dimmedSlides = lp_slider_track.querySelectorAll('.lp-slider-dim');
      dimmedSlides.forEach(slide => slide.classList.remove('lp-slider-dim'));
    }
  </script>
  

</body>
</html>



```


```HTML


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>LP Slider</title>
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: sans-serif;
      background: #111;
    }

    .lp-slider-container {
      width: 100%;
      overflow: hidden;
      padding: 40px 0;
      display: flex;
      justify-content: center;
      position: relative;
    }

    .lp-slider-wrapper {
      width: 1120px; /* 5 slides * (200 + 2*10) = 1120px */
      overflow: hidden;
      position: relative;
    }

    .lp-slider-track {
      display: flex;
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
      transition: opacity 0.3s ease;
    }

    .lp-slider-slide:first-child,
    .lp-slider-slide:last-child {
      opacity: 0.5;
    }

    .lp-slider-dim {
      opacity: 0.3 !important;
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

    .lp-slider-left-arrow {
      left: calc(220px * 1 + 10px); /* 2nd column */
    }

    .lp-slider-right-arrow {
      left: calc(220px * 3 + 10px); /* 4th column */
    }
  </style>
</head>
<body>

  <div class="lp-slider-container">
    <div class="lp-slider-wrapper">
      <div class="lp-slider-track" id="lp_slider_track">
        <div class="lp-slider-slide">1</div>
        <div class="lp-slider-slide">2</div>
        <div class="lp-slider-slide">3</div>
        <div class="lp-slider-slide">4</div>
        <div class="lp-slider-slide">5</div>
      </div>

      <!-- Fixed Arrows -->
      <div
        class="lp-slider-arrow lp-slider-left-arrow"
        id="lp_slider_left_arrow"
        onmouseover="lp_slider_dimColumn(1)"
        onmouseout="lp_slider_resetDim(1)"
        onclick="lp_slider_slideLeft()"
      >&#9664;</div>

      <div
        class="lp-slider-arrow lp-slider-right-arrow"
        id="lp_slider_right_arrow"
        onmouseover="lp_slider_dimColumn(3)"
        onmouseout="lp_slider_resetDim(3)"
        onclick="lp_slider_slideRight()"
      >&#9654;</div>
    </div>
  </div>

  <script>
    const lp_slider_track = document.getElementById('lp_slider_track');

    function lp_slider_slideLeft() {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      const firstSlide = slides[0];
      lp_slider_clearDim();
      lp_slider_track.appendChild(firstSlide);
    }

    function lp_slider_slideRight() {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      const lastSlide = slides[slides.length - 1];
      lp_slider_clearDim();
      lp_slider_track.insertBefore(lastSlide, slides[0]);
    }

    function lp_slider_dimColumn(index) {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      if (slides[index]) {
        slides[index].classList.add('lp-slider-dim');
      }
    }

    function lp_slider_resetDim(index) {
      const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
      if (slides[index]) {
        slides[index].classList.remove('lp-slider-dim');
      }
    }

    function lp_slider_clearDim() {
      const dimmedSlides = lp_slider_track.querySelectorAll('.lp-slider-dim');
      dimmedSlides.forEach(slide => slide.classList.remove('lp-slider-dim'));
    }
  </script>

</body>
</html>


```

<h5>Responsive</h5>

```HTML

<!DOCTYPE html>
<!--[if lt IE 7]>      <html class="no-js lt-ie9 lt-ie8 lt-ie7"> <![endif]-->
<!--[if IE 7]>         <html class="no-js lt-ie9 lt-ie8"> <![endif]-->
<!--[if IE 8]>         <html class="no-js lt-ie9"> <![endif]-->
<!--[if gt IE 8]>      <html class="no-js"> <!--<![endif]-->
<html>
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title></title>
    <meta name="description" content="">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>

      .lp-slider-container {
                    width: 100%;
                    overflow: hidden;
          
                    display: flex;
                    justify-content: center;
                    position: relative;
                  }
              
                  .lp-slider-wrapper {
                    width: 100%;
                    overflow: hidden;
                    position: relative;
                  }
              
                  .lp-slider-track {
                    display: flex;
                    transition: transform 0.5s ease-in-out;
                  }
              
                  .lp-slider-slide {
                    width: 19%;
      
                    margin: 0 10px;
                    color: #fff;
                    font-size: 24px;
                    display: flex;
                    align-items: center;
                    justify-content: center;
                    flex-shrink: 0;
                    border-radius: 10px;
                    position: relative;
                  }
              
          
                  .lp-slider-arrow {
              
                    font-size: 35px;
                    color: rgb(6, 82, 182);
                
               
                    cursor: pointer;
                    z-index: 10;
                    user-select: none;
                  }
                                          
                 .lp-slider-slide img {
                    width: 100%;
                  }
      
                #element-173 a:hover {
                    border: solid 1px #fff;
                }
      
                .btn-arrows {
          display: flex;
          gap: 5px;
          flex-direction: row;
          justify-content: center;
          align-items: center;
      }
      
      .slide-hidden {
        display: none;
      }
      
       @media only screen and (min-width: 912px) {
      
          .lp-slider-slide:first-child,
          .lp-slider-slide:nth-child(5) {
            opacity: 0.2;
          }
            
       }
      
       @media only screen and (min-width: 540px) and (max-width: 912px)  {

      .lp-slider-slide {
        width: 50% !important;
      }
      .lp-slider-track {
        justify-content: center !important;
      }

      }


      @media only screen and (max-width: 540px)  {

      .lp-slider-slide {
        width: 100% !important;
      }
      .lp-slider-track {
        justify-content: center !important;
      }

      }

      
                </style>
  </head>
  <body>
    <!--[if lt IE 7]>
      <p class="browsehappy">You are using an <strong>outdated</strong> browser. Please <a href="#">upgrade your browser</a> to improve your experience.</p>
    <![endif]-->


        
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
<div class="btn-arrows">
<div
class="lp-slider-arrow lp-slider-left-arrow"
id="lp_slider_left_arrow"
onclick="lp_slider_slideLeft()"
>⯇</div>

<div
class="lp-slider-arrow lp-slider-right-arrow"
id="lp_slider_right_arrow"
onclick="lp_slider_slideRight()"
>⯈</div>
</div>

  </div>
</div>

<script>
  const lp_slider_track = document.getElementById('lp_slider_track');
 
   function lp_slider_slideLeft() {
     const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
     const firstSlide = slides[0];
     lp_slider_track.appendChild(firstSlide);
     slideVisibility();
   }
 
   function lp_slider_slideRight() {
     const slides = lp_slider_track.querySelectorAll('.lp-slider-slide');
     const lastSlide = slides[slides.length - 1];
     lp_slider_track.insertBefore(lastSlide, slides[0]);
     slideVisibility();
   }
 
  function slideVisibility() {
 
    const slides =  document.querySelectorAll('.lp-slider-slide');
    let screenWidth = window.outerWidth;
 
    slides.forEach((slide, index) => {
       slide.classList.remove('slide-hidden')
    });
 
    if(screenWidth >= 540 && screenWidth <= 912 ){
 
       // hide slides
       if(slides.length > 0) {
         slides[0].classList.add('slide-hidden');
       }
       if(slides.length > 1) {
        slides[slides.length - 1].classList.add('slide-hidden');
       }
    } else if(screenWidth < 540 ) {
 
      slides.forEach((slide,index) => {
        if(index !== 2) {
           slide.classList.add('slide-hidden');
        }
      })
 
    }
 
  }
 
  slideVisibility();
 
  window.addEventListener('resize', slideVisibility);
 
 
 </script>
         

  </body>
</html>

```

