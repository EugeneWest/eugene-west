<template>
	<div class="work">
		<div class="title_text" ref="title">WORK</div>
	<i class="close-icon fas fa-times"></i>
	<p class='content__heading' ref="eugene">Commercials<br>Challenges<br>Tutorials</p>
	<div class="work_back" @click="startScroll">SCROLL UP</div>
	<div class="work_body" ref="workBody">
		<div class="work__cards">
			<div 
				class="work__card"
				v-for="(workCard) in workCards"
				:key="workCard.id"
				ref="items"
			>
				<div class="work__card__inner">
					<div class="work__card__screen">
					<img class="work__card__website" :src="workCard.img" alt="Eugene West Portfolio">
				</div>
				<div class="work__card__text">
					<p class="work__card__title">{{workCard.title}}</p>
					<p class="work__card__description">{{workCard.description}}</p>
				</div>
				</div>
		</div>
		</div>
	</div>
	</div>
</template>

<script>
import gsap from 'gsap';
import Flip from 'gsap/Flip';
import ScrollTrigger from 'gsap/ScrollTrigger';



export default {

data () {
return {
workCards: [
{id:0, img:require('../assets/chiclu.jpg'), title:'CHICLU', description:'Lorem'},
{id:1, img:require('../assets/chiclu.jpg'), title:'CHICLU', description:'Lorem'},
{id:2, img:require('../assets/chiclu.jpg'), title:'CHICLU', description:'Lorem'},
{id:3, img:require('../assets/chiclu.jpg'), title:'CHICLU', description:'Lorem'},
{id:4, img:require('../assets/chiclu.jpg'), title:'CHICLU', description:'Lorem'},
{id:5, img:require('../assets/chiclu.jpg'), title:'CHICLU', description:'Lorem'},
],
selectedCard: null,
}
},
methods: {
animateTitle () {

const tl =gsap.timeline ({
delay:2,
onComplete: () => {
this.scrollTopWork ();
}

})

tl.fromTo(this.$refs.title, { 
x: -350, 
letterSpacing: '-300px'
}, {
x:0,
ease: 'power4.out',
duration: 1,
stagger: 0.1,
letterSpacing: '0px'

},1)

tl.fromTo(this.$refs.workBody, {yPercent:100}, {yPercent:50},2)

},
doFade (card, active) {
this.selectedCard = card;
const tl = gsap.timeline ({
duration: 1,
onComplete: () => {
const screenInner = card.querySelector('.work__card__inner');
const imageInner = card.querySelector(".work__card__screen");
const textInner = card.querySelector('.work__card__text');
const img = card.querySelector('.work__card__website');
const cardState = Flip.getState([screenInner, imageInner, textInner]);
card.classList.toggle('is__flipped');

Flip.from(cardState, {
				duration: 3,
				absolute: true,
				ease: "power1.inOut",
				onComlete: () => {
gsap.to (img, { duration: 1, ease:"power1.inOut", height: 'fit-content'})
},
				stagger: {
					each: 1,
					from: 0,
					ease: "power1.inOut"
				}
			});

gsap.fromTo('.work__card__description', { xPercent: 100 }, {
	display: 'block' , 
	xPercent: 0 , 
	delay: 5 , 
	duration: 1, 
	ease: "power1.inOut"});
}
})

this.$refs.items.forEach ((card) => {
if (card !== this.selectedCard) {
gsap.to(card, { opacity: 0 })
}
})
tl.to('.work_back', { yPercent: -100, display: "none", duration:1, ease: "power1.inOut" }, 0)
tl.to('.work_body', { backgroundColor: "black", duration:1, ease: "power1.inOut" }, 0)
console.log (active)
console.log (this.selectedCard)

},

doFadeOut (card, active) {
this.selectedCard = card;
const tl = gsap.timeline ({
duration: 1,
onStart: () => {
const screenInner = card.querySelector('.work__card__inner');
const imageInner = card.querySelector(".work__card__screen");
const textInner = card.querySelector('.work__card__text');

const cardState = Flip.getState([screenInner, imageInner, textInner]);
card.classList.toggle('is__flipped');

Flip.from(cardState, {
				duration: 3,
				absolute: true,
				ease: "power1.inOut",
				onComplete: () => {
					this.$refs.items.forEach ((card) => {
						if (card !== this.selectedCard) {
							gsap.to(card, { opacity: 1, duration:1, ease: "power1.inOut" })
						}
						});
					gsap.to('.work_body', { backgroundColor: "white", duration:1, ease: "power1.inOut" });
					gsap.to('.work_back', { yPercent: 0, display: "flex", duration:1, ease: "power1.inOut" }, ">")
				}
			});

gsap.fromTo('.work__card__description', { xPercent: 0 }, {
	display: 'none', 
	xPercent: -100,  
	duration: 1, 
	ease: "power1.inOut"});
}
})
tl.to(card.querySelector(".work__card__screen"), {backgroundColor: "black", duration:1, ease: "power1.inOut"})

console.log (active)
console.log (this.selectedCard)

},

stopStartScroll () {
let trigger = ScrollTrigger.getById("myID");
trigger.scroll(trigger.start)
trigger.disable(false, false)
trigger.animation.progress(1)
},

startScroll () {
let tl = gsap.timeline ({
duration: 1,
onComplete: () => {
let trigger = ScrollTrigger.getById("myID");
trigger.scroll(trigger.start)
trigger.enable()
trigger.animation.progress(0)
}
});
tl.fromTo('.work_back', {yPercent: 0}, { yPercent: -100, display: "none", duration:1, ease: "power1.inOut" })
tl.to(this.$refs.workBody, {yPercent:50, scale: 0.9, duration: 1});
},
scrollTopWork () {

let tl = gsap.timeline({
			onComplete: () => {
				gsap.fromTo('.work_back', {yPercent: -100}, { yPercent: 0, display: "flex", duration: 2.5, ease: "power1.inOut" })
				gsap.to('.work_body', {pointerEvents:"all"});
			},
			scrollTrigger: {
				id: 'myID',
				trigger: '.work',
				scrub: true,
				start: "top top",
				pin: true,
				markers: true,
				onLeave: this.stopStartScroll
			},
		});
		tl.to('.work_body', {yPercent:0});
		tl.to('.work_body', {scale:1});
},


addEventListener () {
const imageWork = document.querySelectorAll('.work__card__website')
imageWork.forEach((image, index) => {
image.addEventListener ('click', () => {
const card = this.$refs.items[index];
this.doFade (card, true);
})
});

const titleWork = document.querySelectorAll('.work__card__title')
titleWork.forEach((title, index) => {
title.addEventListener ('click', () => {
const card = this.$refs.items[index];
this.doFadeOut(card, false);
})
});

const cards = document.querySelectorAll(".card")
cards.forEach((card) => {
card.addEventListener("click", () => {
this.animateTitle ();
});
});

}

},
mounted () {
this.addEventListener ();
}

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


:root {
--index: calc(1vw+1vh);
}
.content__heading {
font-family: FormulaCondensed-Light;
letter-spacing: 5px;
font-weight: 200;
font-size: 54px;
line-height: 1.3;
color: white;
padding-left: 110px;
padding-top: 100px;
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

.title_text {
top: 60px;
font-size: calc(var(--index) * 5);
font-family: raleway-c;
font-weight: 900;
opacity: 15%;
color: white;
position: absolute;
}

.work {
width: 100%;
height: 100%; 
position: absolute;
top: 0;
left: 0;
padding: 60px;
overflow: hidden;
}
.work_back {
position: fixed;
top: 0;
left: 0;
display: none;
justify-content: center;
width: 100vw;
height: 80px;
padding: 20px;
background-color: bisque;
align-items: center;
z-index: 1000;
}
.work_body {
position: absolute;
display: flex;
flex-direction: column;
justify-content: flex-end;
align-items: flex-end;
height: 100%;
width: 100%;
background-color: white;
overflow: hidden;
transform: scale(0.9);
left: 0;
top:0;
pointer-events: none;
}

.work_footer {
display: flex;
flex-direction: row;
justify-content: flex-start;
align-items: flex-end;
gap: 40px;
height: 200px;
width: 100%;
background-color: black;
}

/*start - Work cards */

.text-block {
color: var(--color-text);
position: relative;
gap: 30px;
display: flex;
flex-direction: column;

}

.work__cards {
overflow: scroll;
display: grid;
grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
grid-auto-rows: 300px;
width: 100%;
height: fit-content;
padding: 60px;
gap: calc(var(--index) * 10);
margin-bottom: 60px;
}

.work__card {
width: 290px;
height: 280px;
flex: 0 0 auto;
}

.work__card__inner {
will-change: transform;
width: 290px;
height: 280px;
background-color: black;
overflow: hidden;
display: flex;
flex-direction: column;
padding: 16px;

}

.work__card__screen {
overflow:hidden;
width:100%;
height:65%;
max-width: 260px;
position: relative;
}

.work__card__website {
will-change: transform;
position: relative;
filter: grayscale(1);
-webkit-filter: grayscale(100%);
top: 0;
left: 0;
width: 100%;
height: 100%;
object-fit:cover;
transition: transform 0.3s filter 0.5s ease-in-out;
object-position: top;
}

.work__card__website:hover {
filter: none;
-webkit-filter: grayscale(0%);
}

.work__card__text {
display: flex;
align-items: flex-start;
flex-direction: column;
width:100%;
height:auto;
padding-top: 16px;
}

.work__card__description {
font-family: raleway-regular;
letter-spacing: 5px;
font-weight: 200;
font-size: 20px;
line-height: 1.3;
color: white;
display: none;
}

.work__card__title {
font-size: calc(var(--index) * 1.2);
font-family: FormulaCondensed-Light;
letter-spacing: 5px;
font-weight: 300;
color: white;
}

.work__card.is__flipped .work__card__inner {
position: absolute;
top: 0;
right: 0;
bottom: 0;
left: 0;
width: 100%;
height: 100%;
z-index: 1000;
display: flex;
flex-direction: row;
padding: 0px;
gap: 20px;
}
.work__card.is__flipped .work__card__screen {
max-width: none;
height: 100vh;
overflow: scroll;
}

.work__card.is__flipped .work__card__website {
will-change: transform;
position: relative;
top: 0;
left: 0;
width: 50vw;
height: fit-content;
object-fit:cover;
transition: transform 0.3s;
filter: none;
}



/*end - Work cards */

</style>

