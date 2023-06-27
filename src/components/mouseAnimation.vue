<template>
	<div class="cursor" ref="cursor"></div>
	<div class="ball" ref="ball"></div>
</template>

<script>
import gsap from 'gsap';
import Flip from 'gsap/Flip';


export default {

methods: {

addEventListener () {
document.addEventListener ('click', () => {
gsap.to(this.$refs.ball, {ease: "power1.inOut", height: "14px", width: '14px', duration: 1})
gsap.to(this.$refs.ball, {ease: "power1.inOut", height: "10px", width: '10px', duration: 1})
})
},

flipMouse () {

//Get current states
const ballState = Flip.getState(this.$refs.ball);
const cursorState = Flip.getState(this.$refs.cursor)

// Toggle the active class on the card element
this.$refs.ball.classList.toggle('white');
 this.$refs.cursor.classList.toggle('white');


 Flip.from(ballState, {
		duration: 0.1,
		ease: "power1.inOut",
		simple: false,
		fade:true,
		absolute: true
	})
 Flip.from(cursorState, {
	duration: 0.1,
	ease: "power1.inOut",
	simple: false,
	fade:true,
	absolute: true
 });

 gsap.set(this.$refs.ball, { xPercent: -50, yPercent: -50 });
 gsap.set(this.$refs.cursor, { xPercent: -50, yPercent: -50 });
//const cards = document.querySelectorAll(".card__image");
//const icons = document.querySelectorAll(".close-icon");


//cards.forEach((card) => {
//  card.addEventListener("mouseenter", () => {
//    playMouse ();
//});
//})

//icons.forEach((icon) => {
//  icon.addEventListener("click", () => {
//    playMouse ();
//});
//});

	
},
animateMouse () {

	//start - curson animation//
	const portfolioElement = document.querySelector('.portfolio');
	const portfolioStyle = window.getComputedStyle(portfolioElement);

		if(portfolioStyle.transform === 'none') {
			gsap.set(this.$refs.ball, { xPercent: -50, yPercent: -50 });
			gsap.set(this.$refs.cursor, { xPercent: -50, yPercent: -50 });
		
			let cxTo = gsap.quickTo(this.$refs.cursor, "x", { duration: 0.2, ease: "power3"}),
			cyTo = gsap.quickTo(this.$refs.cursor, "y", { duration: 0.2, ease: "power3"});
		
			let xTo = gsap.quickTo(this.$refs.ball, "x", {duration: 0.2, ease: "power3"}),
			yTo = gsap.quickTo(this.$refs.ball, "y", {duration: 0.2, ease: "power3"});
		
			window.addEventListener("mousemove", e => {
			
				if (this.$refs.cursor) {
				this.$refs.cursor.classList.remove('hidden')
	}
				if (this.$refs.ball) {
				this.$refs.ball.classList.remove('hidden')
	}


				cxTo(e.clientX);
				cyTo(e.clientY);

				xTo(e.clientX);
				yTo(e.clientY);


			})
		
			window.addEventListener("mouseout", () => {
				if (this.$refs.cursor) {
				this.$refs.cursor.classList.add('hidden')
	}
				if (this.$refs.ball) {
				this.$refs.ball.classList.add('hidden')
	}
	});
		}
	//end - curson animation//
}

},

mounted () {
this.addEventListener ();
this.animateMouse ();


const cards = document.querySelectorAll(".card__image");
const icons = document.querySelectorAll(".close-icon");
const work = document.querySelector(".work_body");
const workCards = document.querySelectorAll(".work__card");

cards.forEach((card) => {

card.addEventListener("click", () => {
this.flipMouse ();
});
})

cards.forEach((card) => {
card.addEventListener("mouseenter", () => {
 this.flipMouse ();
});
})

cards.forEach((card) => {
card.addEventListener("mouseleave", () => {
 this.flipMouse ();
});
})

icons.forEach((icon) => {
icon.addEventListener("click", () => {
 this.flipMouse ();
});
});

work.addEventListener ('mouseenter', () => {
this.flipMouse ();
});

workCards.forEach((card) => {
card.addEventListener("mouseenter", () => {
 this.flipMouse ();
});
})

workCards.forEach((card) => {
card.addEventListener("mouseleave", () => {
 this.flipMouse ();
});
})


}

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* start - cursor */
.cursor {
will-change: transform;
z-index: 2000;
transition: .5s cubic-bezier(.75, 1.27, .3, 2.33) transform, .2s cubic-bezier(.75, 1.27, .3, 2.33) opacity;
width: 40px;
height: 40px;
position: fixed;
top: 0;
left: 0;
border: 1px solid rgb(0, 0, 0);
border-radius: 100%;
pointer-events: none;
}


.ball {
will-change: transform;
z-index: 2000;
width: 10px;
height: 10px;
position: fixed;
top: 0;
left: 0;
background: #000000;
border: 1px solid rgb(0, 0, 0);
border-radius: 100%;
pointer-events: none;
}


.ball.white {
background: #fff;
}

.cursor.white {
border: 1px solid rgb(255, 255, 255);
}

.hidden {
visibility: hidden;
opacity: 0;
transition: visibility 0.5s, opacity 0.5s linear;
}

/* end cursor */
</style>

