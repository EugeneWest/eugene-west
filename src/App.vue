
<!-- HTML -->
<template>

  <div class="tv"> 
    <img class="screen_1" src= "./assets/tv/tv-1.png">
    <img class="screen_2" src= "./assets/tv/tv-2.png">
    <div class="video">
          <video id="bgvid" playsinline autoplay muted loop>
            <source src="https://db6a5274acf1962e5c278326eaaa76b4.cdn.bubble.io/f1684337249481x585652847600613100/Untitled%20design%20%281%29.mp4" type="video/mp4">
          </video>
     </div>
    <div class="content_tv">
    <canvas id="canvas"></canvas>	
          <div class="counter">
            <h1>0%</h1>
        </div>
        <div class="portfolio">
          <animateMouse></animateMouse>
         <div class="title">
           <h2>EUGENE WEST</h2>
           <div class="nav">
             <div class="nav__text">ABOUT</div>
             <div class="nav__text">SERVICE</div>
             <div class="nav__text">WORK</div>
             <div class="nav__text">EXPERIENCE</div>
             <div class="nav__text">CONTACT</div>
           </div>
         </div>
         
         <div class="cards">
             <div
               class="card"
               v-for="card in cards"
               :key="card.id"
               :ref="`card-${card.id}`"
             >
               <div class="card__inner">
                 <div class="card__image">
                  <div class="card_text">{{ card.text }}</div>
                 </div>
               </div>
             </div>
           </div>
  
           <div class="social">
            <div class="social__icons">
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 50 50" width="24px" height="24px">    <path d="M41,4H9C6.24,4,4,6.24,4,9v32c0,2.76,2.24,5,5,5h32c2.76,0,5-2.24,5-5V9C46,6.24,43.76,4,41,4z M17,20v19h-6V20H17z M11,14.47c0-1.4,1.2-2.47,3-2.47s2.93,1.07,3,2.47c0,1.4-1.12,2.53-3,2.53C12.2,17,11,15.87,11,14.47z M39,39h-6c0,0,0-9.26,0-10 c0-2-1-4-3.5-4.04h-0.08C27,24.96,26,27.02,26,29c0,0.91,0,10,0,10h-6V20h6v2.56c0,0,1.93-2.56,5.81-2.56 c3.97,0,7.19,2.73,7.19,8.26V39z"/></svg>
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 72 72" width="24px" height="24px"><path d="M 43.818359 7.8652344 L 40.195312 10.560547 L 53.671875 28.679688 L 57.294922 25.984375 L 43.818359 7.8652344 z M 35.509766 15.076172 L 32.619141 18.546875 L 49.970703 32.996094 L 52.859375 29.525391 L 35.509766 15.076172 z M 28.861328 24.494141 L 26.955078 28.587891 L 47.421875 38.119141 L 49.328125 34.027344 L 28.861328 24.494141 z M 24.960938 34.748047 L 24.03125 39.167969 L 46.126953 43.8125 L 47.054688 39.394531 L 24.960938 34.748047 z M 14.630859 40.505859 L 14.630859 58.5 L 55.119141 58.5 L 55.119141 40.505859 L 50.619141 40.505859 L 50.619141 54.001953 L 19.128906 54.001953 L 19.128906 40.505859 L 14.630859 40.505859 z M 23.626953 45.003906 L 23.626953 49.503906 L 46.119141 49.503906 L 46.119141 45.003906 L 23.626953 45.003906 z"/></svg>
              <svg xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" width="24px" height="24px">    <path d="M10.9,2.1c-4.6,0.5-8.3,4.2-8.8,8.7c-0.5,4.7,2.2,8.9,6.3,10.5C8.7,21.4,9,21.2,9,20.8v-1.6c0,0-0.4,0.1-0.9,0.1 c-1.4,0-2-1.2-2.1-1.9c-0.1-0.4-0.3-0.7-0.6-1C5.1,16.3,5,16.3,5,16.2C5,16,5.3,16,5.4,16c0.6,0,1.1,0.7,1.3,1c0.5,0.8,1.1,1,1.4,1 c0.4,0,0.7-0.1,0.9-0.2c0.1-0.7,0.4-1.4,1-1.8c-2.3-0.5-4-1.8-4-4c0-1.1,0.5-2.2,1.2-3C7.1,8.8,7,8.3,7,7.6C7,7.2,7,6.6,7.3,6 c0,0,1.4,0,2.8,1.3C10.6,7.1,11.3,7,12,7s1.4,0.1,2,0.3C15.3,6,16.8,6,16.8,6C17,6.6,17,7.2,17,7.6c0,0.8-0.1,1.2-0.2,1.4 c0.7,0.8,1.2,1.8,1.2,3c0,2.2-1.7,3.5-4,4c0.6,0.5,1,1.4,1,2.3v2.6c0,0.3,0.3,0.6,0.7,0.5c3.7-1.5,6.3-5.1,6.3-9.3 C22,6.1,16.9,1.4,10.9,2.1z"/></svg>
              <svg width="18" height="20" viewBox="0 0 18 20" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M16.3995 12.5647C16.3995 15.6997 13.9029 18.1993 10.8743 18.1993C7.84565 18.1993 5.34902 15.6997 5.34902 12.5647C5.34902 9.42971 7.84565 6.93008 10.8743 6.93008C13.9029 6.93008 16.3995 9.42971 16.3995 12.5647Z" stroke="black" stroke-width="3.2"/><path d="M3.74902 0H7.34902V7.61538L3.74902 12.9462V0Z" fill="black"/><ellipse cx="1.87506" cy="17.896" rx="1.87506" ry="1.90385" fill="black"/></svg>
            </div>
            <h3>Eugene West ©︎ 2023</h3>
         </div>
         
         <div class='content'>
           <div class='content__group'><aboutMe /></div>
           <div class='content__group'>
             <i class="close-icon fas fa-times"></i>
             <p class='content__heading'>SERVICE</p>
             <p class='content__category'>Horror</p>
             <p class='content__description'>
               Cras justo odio, dapibus ac facilisis in, egestas eget quam. Donec sed odio dui.
             </p>
           </div>
         
           <div class='content__group'><myWork /></div>
  
           <div class='content__group'>><expMe /></div>
  
           <div class='content__group'>
                   <i class="close-icon fas fa-times"></i>
             <p class='content__heading'>CONTACT</p>
             <p class='content__category'>Psychological Thriller</p>
             <p class='content__description'>
               Cras justo odio, dapibus ac facilisis in, egestas eget quam. Donec sed odio dui.
             </p>
           </div>
         
         </div>
        </div>
    </div>
    <img class="screen_4" src= "./assets/tv/tv-3.png">
  </div>
  
  
  </template>
  
  
  
  <!-- JS -->
  <script>
  import gsap from 'gsap';
  import Flip from 'gsap/Flip';
  import ScrollTrigger from 'gsap/ScrollTrigger';
  gsap.registerPlugin(ScrollTrigger);
  
  import animateMouse from './components/mouseAnimation.vue'
  import aboutMe from './components/aboutMe.vue'
  import myWork from './components/myWork.vue'
  import expMe from './components/expMe.vue'
  
  export default {
    components: {
      animateMouse,
      aboutMe,
      myWork,
      expMe
    },
    data () {
      return {
        cards: [
          { id: 1, text: "ABOUT" },
          { id: 2, text: "SERVICE" },
          { id: 3, text: "WORK" },
          { id: 4, text: "EXPERIENCE" },
          { id: 5, text: "CONTACT" },
        ],
        active:true,
        showElement: false
      }
    },
    methods: {
      animate (card, idx, active) {
        
        const textContent = document.querySelectorAll(".card_text")[idx];
        const cardContent = document.querySelectorAll(".content__group")[idx];
        let tl = gsap.timeline ({
          
          onStart: () => {
  
            const mainContent = document.querySelector(".content");
            //const cardContent = document.querySelectorAll(".content__group")[idx];
            const cardInner = card.querySelector('.card__inner')
            const image = card.querySelector(".card__image");
  
            //Stap Flip
            const cardState = Flip.getState(cardInner, {props: "transform, width, height, border-radius"});
            const imageState = Flip.getState(image, {props:"transform, border-radius, width, height"});
  
            // Toggle the active class on the card element
                  card.classList.toggle('is-active');
  
                     if (!active) {
                    gsap.to(mainContent, {
                    display: "none"
                    });
                    ScrollTrigger.killAll( ) ;
  
            }
                    if (active) {
                    
                    gsap.to(mainContent, {
                    display: "block"
                });
                  }
                
                  Flip.from(cardState, {
                        duration: 1,
                        ease: "power1.inOut",
                        absolute: true,
                        zIndex: 1
                      });
  
                  Flip.from(imageState, {
                   duration: 1,
                   absolute: true,
                   ease: "power1.inOut",
                   simple: true
                 });
          }
        })
  
        tl.killTweensOf(textContent);
        tl.to(textContent, {
          ease: "expo.out",
          y: active ? -1000: 0,
          duration: active ? 1 : 1,
          delay: active ? 0: 1,
    });
         tl.killTweensOf(cardContent);
         tl.fromTo(cardContent, {alpha: active ? 1 : 0, ease: "back.out(1.7)", delay: active ? 1 : 0, x: active ? -2000 : 0}, 
           {delay: active ? 1 : 0,
            zIndex: active ? 1000 : 1,
            x: active ? 0 : -2000,
            duration: 1,
           }
         );
   
  
      },
  
      animateTv () {
  
      //start- tv animation//
      let canvas = document.getElementById('canvas'),
      ctx = canvas.getContext('2d');
  
  let w = ctx.canvas.width,
      h = ctx.canvas.height,
      idata = ctx.createImageData(w, h),
      buffer32 = new Uint32Array(idata.data.buffer),
      len = buffer32.length,
      i = 0;
  
  function resize() {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
  
      w = ctx.canvas.width;
      h = ctx.canvas.height;
      idata = ctx.createImageData(w, h);
      buffer32 = new Uint32Array(idata.data.buffer);
      len = buffer32.length;
  }
  resize();
  window.onresize = resize;
  
  function noise(ctx) {
  
      for(i=0; i < len;) {
          buffer32[i++] = ((255 * Math.random())|0) << 24;
      }
  
      ctx.putImageData(idata, 0, 0);
  }
  
  let toggle = true;
  
  // added toggle to get 30 FPS instead of 60 FPS
  (function loop() {
      toggle = !toggle;
      if (toggle) {
          noise(ctx);
      }
      requestAnimationFrame(loop);
  })();
  
  let counter = 0;
      let c = 0;
      let h1 = document.querySelector('.counter h1');
      
  
      function tvoff () {
                console.log ('Run');
                gsap.fromTo(".video", {display:"block"}, {display:"none", duration:1});
                gsap.to(".counter", { display: "none", duration: 0.5 });
                gsap.to(".portfolio", { display: "flex", duration: 0.5 });
              }
  
  
      let ii = setInterval(function() {
          h1.innerHTML = c + '%';
          
          counter++;
          c++;
          if (counter === 101) {
  
              clearInterval(ii);
              h1.textContent = "scroll";
              document.body.style.overflow = 'scroll';
              
  
              let tl = gsap.timeline({
                scrollTrigger: {
                  trigger: ".tv",
                  scrub: true,
                  start: "top top",
                  pin: true,
                  once:true
                },
              });
  
              tl.fromTo ('.portfolio', {scale: 0.34, top:'14%'}, {scale:1, top: 0}, 0);
              tl.fromTo('.screen_1', { scale: 1 }, { scale: 10, transformOrigin: '50% 60%' },0)
              tl.fromTo('.screen_2', { scale: 1 }, { scale: 10, transformOrigin: '50% 60%' },0)
              tl.fromTo('.screen_4', { scale: 1 }, { scale: 10, transformOrigin: '50% 60%' },0)
              tl.to(canvas, { opacity: 0, display: "none" });
              tl.to(".content_tv", { zIndex: 100 });
              
  
              let hasScrolled = false;
  
              window.addEventListener("scroll", () => {
                if (window.pageYOffset > 50 && !hasScrolled) {
                  tvoff(false); // Call the tvoff function when the scroll position is greater than 50 and hasScrolled is false
                  hasScrolled = true; // Set the flag to true after the code is executed
                }
              });
          }
      }, 50);
              //end - tv animation//
  
  
      }
    },
  
    //mount starts here
    mounted () {
      
      this.animateTv ();
  
  //start- card animation triggers//
  const activeClass = "is-active";
  const cards = document.querySelectorAll(".card")
  const icons = document.querySelectorAll(".close-icon");
  const navs = document.querySelectorAll(".nav__text");
  
  navs.forEach((nav, idx) => {
    nav.addEventListener("click", () => {
      const card = cards[idx];
      this.animate(card, idx, true);
      console.log ("Nav")
      console.log (idx)
    });
  });
  
  icons.forEach((icon, idx) => {
    icon.addEventListener("click", () => {
      const card = cards[idx];
      this.animate(card, idx, false);
      console.log ("Icon")
      console.log (idx)
    });
  });
  
  cards.forEach((card, idx) => {
    
    card.addEventListener("click", () => {
  
      this.animate(card, idx, !card.classList.contains(activeClass));
      
    });
  })
  //end- card animation triggers//
    }
  }
   
    
  </script>
  
  <!-- CSS -->
  <style>
  
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    box-sizing: border-box;
    background-color: var(--background-color);
  }
  body {
    overflow: hidden;
  }
  .portfolio {
    position: fixed;
    background-color: white;
    padding: 60px;
    cursor: none;
    display: none;
    align-items: center;
    flex-direction: row;
    justify-content: space-between;
    width: 100%;
    height: 100%;
    z-index: 3;
    transition: all .5s ease-in-out;
  }
  
  :root {
    --background-color: #fff;
    --selection-color: ;
    --index: calc(1vw+1vh);
  }
  
  @font-face {
    font-family: raleway-c;
    src: url(assets/fonts/raleway-regular.woff2);
  }
  
  @font-face {
    font-family: outfit-c;
    src: url(assets/fonts/outfit-regular.woff2);
  }
  
  @font-face {
    font-family: formula;
    src: url(assets/fonts/FormulaCondensed-Light.otf);
  }
  
  @font-face {
    font-family: Akkurat;
    src: url(assets/fonts/FontsFree-Net-Akkurat.woff2.ttf);
  }
  
  h2, h4, h5 {
    font-family: FormulaCondensed-Light;
    letter-spacing: 5px;
    font-weight: 200;
    font-size: calc(var(--index) * 5);
    line-height: 1.3;
    color: #000000;
    width: fit-content;
  }
  
  h3 {
    font-family: FormulaCondensed-Light;
    letter-spacing: 5px;
    font-weight: 200;
    font-size: 16px;
    line-height: 1.3;
    color: #000000;
    width: fit-content;
  }
  
  .p {
    font-family: Akkurat;
    letter-spacing: 1px;
    font-weight: 100;
    font-size: 20px;
  }
  
  .card_text {
    font-family: FormulaCondensed-Light;
    letter-spacing: 0.1em;
    font-weight: 300;
    font-size: 14px;
    line-height: 43px;
    position: absolute;
    transform: perspective(800px) rotateY(20deg);
    color: white;
    z-index: 4;
  }
  
  .nav__text {
    font-family: FormulaCondensed-Light;
    letter-spacing: 0.1em;
    font-weight: 300;
    font-size: 36px;
    line-height: 43px;
    color: #000000;
    width: fit-content;
  }
  
  .nav__text:hover {
    text-decoration: underline;
    transition: 300ms;
  }
  
  *,
  *:before,
  *:after {
    box-sizing: inherit;
    margin: 0px;
  }
  
  a {
    color: inherit;
    text-decoration: none;
  }
  
  img,
  svg {
    display: block;
    max-width: 100%;
    height: auto;
  }
  
  ::selection {
    background: var(--selection-color);
    color: white;
    text-shadow: none;
  }
  
  
  
  .cards {
    margin: auto 0;
    width: 150px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
  }
  @media (min-width: 768px) {
    .cards {
      width: 640px;
    }
  }
  
  .card,
  .card__inner,
  .card__image {
    width: 150px;
    height: 150px;
  }
  @media (min-width: 768px) {
    .card,
  .card__inner,
  .card__image {
      width: 105px;
      height: 130px;
    }
  }
  
  .card {
    flex: 0 0 auto;
    margin: 10px;
  }
  
  .card__inner {
    will-change: transform;
    background-color: white;
    border-radius: 5px;
  }
  
  .card__image {
    position: absolute;
    will-change: transform;
    display: flex;
    align-items: center;
    justify-content: center;
    transform-origin: center;
    transform: perspective(800px) rotateY(20deg);
    transition: transform 0.5s, opacity 0.5s;
    -webkit-box-reflect: below 1px linear-gradient(transparent, transparent, #0004);
    background-color: #000000;
    border-radius: 5px;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center center;
  }
  
  
  
  .card__image:hover {
    transform: scale(1.1);
  }
  
  
  
  
  .is-active {
    position: absolute;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    margin: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    border-radius: 0;
    will-change: transform;
  }
  .card.is-active .card__image {
    width: 100vw;
    height: 100vh;
    will-change: transform;
    position: absolute;
    top: 0;
    left: 0;
    transform: none;
    border-radius: 0px;
  }
  
  /* start - content */
  .content {
    top: 0;
    left: 0;
    position: absolute;
    display: none;
    width: 100vw;
    height: 100vh;
  }
  
  .content__group {
    width: 100%;
    height: 100%;
    opacity: 0;
    position: absolute;
    display: flex;
    flex-direction: column;
    justify-content: center;
    z-index: 2;
    padding: 60px;
    overflow: auto;
    top: 0;
    left: 0;
  }
  
  
  
  .content__heading {
    font-family: FormulaCondensed-Light;
    letter-spacing: 5px;
    font-weight: 200;
    font-size: 54px;
    line-height: 1.3;
    color: white;
  }
  
  
  .content__category {
    background-color: cadetblue;
    display: inline-block;
    color: rgba(255, 255, 255, 0.8);
    font-size: 14px;
    padding: 0 12px;
    line-height: 30px;
    border-radius: 15px;
    align-self: flex-start;
    margin-top: 8px;
  }
  
  .content__description {
    font-family: Akkurat;
    font-weight: 200;
    font-size: 17px;
    line-height: 1.5;
    margin-top: 55px;
    color: white;
  }
  
  
  
  
  .close-icon {
    top: 80px;
    right: 80px;
    color: white;
    cursor: none;
    display: block;
    font-size: 14px;
    position: absolute;
  }
  
  .close-icon:hover {
    opacity: 0.8;
    font-size: 20px;
  }
  
  
  /* end - content */
  
  
  
  
  /* start - title */
  .title {
    flex-direction: column;
    width: fit-content;
    height: 100%;
    display: flex;
  
  }
  
  .nav {
    margin-top: 170px;
    display: flex;
    flex-direction: column;
    gap: 16px;
  }
  /* end - title */
  
  /* start - social */
  .social__icons {
    flex-direction: row;
    width: fit-content;
    gap: 16px;
    display: flex;
  }
  .social {
    align-items: flex-end;
    flex-direction: column;
    width: fit-content;
    height: 100%;
    display: flex;
    justify-content: space-between;
  }
  /* end - social */
  
  /*start - TV and Loader styles */
  .tv {
    background-color: black;
    width: 100vw;
    height: 100vh;
    position: fixed;
  }
  
  .screen_1 {
    z-index: 5;
    position: fixed;
    opacity: 0.5;
    width: 100%;
    height: 100%;
    transition: all .5s ease-in-out;
  
  }
  
  .screen_2 {
    z-index: 4;
    position: fixed;
    width: 100%;
    height: 100%;
    transition: all .5s ease-in-out;
  }
  
  .screen_4 {
    z-index: 1;
    position: fixed;
    width: 100%;
    height: 100%;
    transition: all .5s ease-in-out;
  }
  
  .content_tv {
    z-index: 2;
    position: fixed;
    width: 100vw;
    height: 100vh;
    transition: all 1s ease-in-out;
  }
  
  canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: 5;
    transition: all 1s ease-in-out;
  }
  h1 {
    font-family: FormulaCondensed-Light;
    letter-spacing: 5px;
    font-weight: 200;
    text-transform: uppercase;
    font-size: 54px;
    text-align: center;
    line-height: 1.3;
    position: relative;
    z-index: 999;
    mix-blend-mode: difference;
    color: white;
    text-shadow: 0 -5px 2px rgba(255, 51, 51, 0.2),
      -5px -5px 2px rgba(255, 51, 51, 0.2), 0 5px 2px rgba(0, 255, 255, 0.2),
      5px 5px 2px rgba(0, 255, 255, 0.2);
    position: relative;
    animation: 2s out-of-focus infinite;
  }
  @keyframes out-of-focus {
    55% {
      filter: blur(0);
      opacity: 1;
    }
    59% {
      left: 0;
    }
    60% {
      filter: blur(2px);
      left: -2px;
    }
    61% {
      filter: blur(0);
      left: 2px;
      top: 2px;
      opacity: 0.5;
    }
    62% {
      filter: blur(2px);
      left: 0;
      top: 0;
      opacity: 1;
    }
    70% {
      filter: blur(0);
    }
  }
  
  .counter {
      position: fixed;
      display: flex;
      flex-direction: column;
      justify-content: center;
      z-index: 4;
      width: 50%;
      height: 50%;
      top: 39%;
      left: 26%;
  }
  
  
  
  .video {
    z-index: 3;
    position: fixed;
    width: 100%;
    height: 100%;
    display: none;
  }
  
  video { 
      position: fixed;
      top: 50%;
      left: 50%;
      min-width: 100%;
      min-height: 100%;
      width: auto;
      height: auto;
      z-index: -100;
      transform: translateX(-50%) translateY(-50%);
  }
  
  /* end - TV and Loader styles */
  
  </style>
  