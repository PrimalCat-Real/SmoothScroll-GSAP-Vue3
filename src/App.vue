<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://vuejs.org/api/sfc-script-setup.html#script-setup
import HelloWorld from './components/HelloWorld.vue'
</script>

<script>
gsap.registerPlugin(ScrollSmoother, ScrollTrigger)
gsap.timeline({
    // yes, we can add it to an entire timeline!
    scrollTrigger: {
      trigger: ".nav-header",
      pin: true,   // pin the trigger element while active
    
    }
  });

// add animations and labels to the timeline

let smoother = ScrollSmoother.create({
    wrapper: '.wrapper',
    content: '.content',
    smooth: 3,
})

gsap.to('progress', {
  value: 100,
  ease: 'none',
  scrollTrigger: { scrub: 0.3 }
});


export default{
  methods: {
    scrollToBox: function (event) {
      // `this` внутри методов указывает на экземпляр Vue
      // `event` — нативное событие DOM
      smoother.scrollTo('.box-c', true, 'center center')
    }
  }
}
</script>

<template>
  <div>
    <header class="nav-header">
      <h1 class="title">ScrollSmoother</h1>
      <button class="button" v-on:click="scrollToBox">Jump to C</button>
    </header>
    <div class="box box-a" data-speed="0.5">a</div>
    <div class="box box-b" data-speed="0.8">b</div>
    <div class="box box-c" data-speed="1.5">c</div>
    <div class="line"></div>
  </div>
 
    
</template>

<style>

:root {
	--dark: #1d1d1d;
  --grey-dark: #414141;
	--light: #fff;
	--mid: #ededed;
  --grey: #989898;
  --gray: #989898;
	--green: #28a92b;
  --green-dark: #4e9815;
	--green-light: #6fb936;
	--blue: #2c7ad2;
	--purple: #8d3dae;
	--red: #c82736;
	--orange: #e77614;
  accent-color: var(--green);
}
progress {
  position: fixed;
  top: 0;
  left: 0;
  -webkit-appearance: none;
  appearance: none;
  width: 100%;
  height: 15px;
  border: none;
  background: transparent;
}
.test1{
  display: flex;
}
body {
  background-color: #111;
  font-family: "Signika Negative", sans-serif, Arial;
  overscroll-behavior: none;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}
#smooth-content {
  overflow: visible;
  width: 100%;
  /* set a height because the contents are position: absolute, thus natively there's no height */
  height: 4000px;

  background-image:
    linear-gradient(rgba(255,255,255,.07) 2px, transparent 2px),
    linear-gradient(90deg, rgba(255,255,255,.07) 2px, transparent 2px),
    linear-gradient(rgba(255,255,255,.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,.06) 1px, transparent 1px);
  background-size: 100px 100px, 100px 100px, 20px 20px, 20px 20px;
  background-position: -2px -2px, -2px -2px, -1px -1px, -1px -1px;
}
.end {
  position: absolute;
  /*   bottom: 0; */
  top: 2400px;
  transform: translateY(-100%);
  font-size: 30px;
  color: white;
}

/* button:not('.box') { breaking for some reason in codepen? */
button {
	display: inline-block;
	outline: none;
	border: none;
	padding: 8px 14px;
	background: var(--light);
  background-image: linear-gradient(to bottom, hsl(0deg 0% 100%), hsl(0deg 0% 94%));
	-webkit-box-shadow: 0px 1px 0px #414141;
	-moz-box-shadow: 0px 1px 0px #414141;
	box-shadow: 0px 1px 0px #414141;
	color: var(--dark);
	text-decoration: none;
	-webkit-border-radius: 4;
	-moz-border-radius: 4;
	border-radius: 4px;
	padding: 12px 25px;
	font-family: "Signika Negative", sans-serif;
	text-transform: uppercase;
	font-weight: 600;
	cursor: pointer;
	line-height: 18px;
}

.light button {
    color: var(--light);
  	background-image: linear-gradient(to bottom, #575757, #414141);
}

button:hover {
	background: var(--green-light);
	background-image: linear-gradient(to bottom, #57a818, #4d9916);
	-webkit-box-shadow: 0px 1px 0px fefefe;
	-moz-box-shadow: 0px 1px 0px fefefe;
	box-shadow: 0px 1px 0px fefefe;
	color: #ffffff;
	text-decoration: none;
}
button {
  position: relative; 
}

.box {
  width: 100px;
  height: 100px;
  background-color: #28a92b;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  z-index: 100;
  line-height: 100px;
  font-size: 50px;
  text-align: center;
  will-change: transform;
}
.box.active {
  background-color: red;
}

.box-a {
  top: 200px;
  background-color: #8d3dae;
}

.box-b {
  top: 600px;
}

.box-c {
  top: 1000px;
  background-color: #e26c16;
}

.line {
  visibility: hidden;
  width: 2px;
  height: 4000px;
  position: absolute;
  left: 400px;
  top: 0px;
  background-color: #777;
}

header .name {
  color: white;
}

.title {
  text-align: center;
  color: white;
  font-weight: 400;
  font-size: 40px;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
