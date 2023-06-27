<template>
	<div class="title_text" ref="title">ABOUT</div>
	<i class="close-icon fas fa-times"></i>
	<p class='content__heading' ref="eugene">Hi,<br>I'm Eugene West</p>
	<div class="me">
		<div class="me_1">
			<p class='about__description'>
				Low / No-code Engineer with a passion for solving problems and helping others.
			</p>
			<p class='about__description'>
				I’ve been doing it for 3 years.
			</p>
			<p class='about__description'>
				I also have 1 year of experience as a front-end developer.
			</p>
			<p class='about__description'>
				As a troubleshooter and consultant, I enjoy collaborating with other developers to find creative solutions to complex challenges.
			</p>
		</div>
	<img class="photo" src="../assets/me.jpg" alt="Eugene West">
	</div>
</template>

<script>
import gsap from 'gsap';


export default {

methods: {
animateTitle () {

const tl =gsap.timeline ({delay:2})

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

},
},
mounted () {
const cards = document.querySelectorAll(".card")

cards.forEach((card) => {

card.addEventListener("click", () => {

this.animateTitle ();

});
})


}

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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


.about__description {
font-family: Akkurat;
font-weight: 200;
font-size: 18px;
line-height: 1.5;
width: 100%;
height: fit-content;
color: white;
background-color: rgba(255, 255, 255, 0.15);
padding: 16px;
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
font-size: calc(var(--index) * 10.5);
font-family: raleway-c;
font-weight: 900;
opacity: 15%;
color: white;
position: absolute;
}

.me {
display: flex;
flex-direction: row;
justify-content: flex-start;
align-items: flex-end;
gap: 40px;
max-height: 400px;
width: 100%;
padding-left: 160px;
}

.me_1 {
display: flex;
flex-direction: column;
justify-content: flex-end;
align-items: flex-start;
gap: 16px;
max-height: 400px;
max-width: 667px;
}

.photo {
max-width: 300px;
}
</style>

