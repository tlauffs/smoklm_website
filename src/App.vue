<script setup>
import Hero from "./components/Hero.vue";
import Youtube from "./components/Youtube.vue";
import Navigation from "./components/Navigation.vue";
import { ref } from "vue";

const blobleft = ref("50%");
const blobtop = ref("50%");

const tab = ref("home");

let mouseX = window.innerWidth / 2;
let mouseY = window.innerHeight / 2;
let blobX = window.innerWidth / 2;
let blobY = window.innerHeight / 2;
let speed = 0.02;

function animate() {
  let distX = mouseX - blobX;
  let distY = mouseY - blobY;
  blobX = blobX + distX * speed;
  blobY = blobY + distY * speed;
  blobleft.value = blobX + "px";
  blobtop.value = blobY + "px";
}
setInterval(animate, 10);

document.addEventListener("pointermove", function (event) {
  mouseX = event.pageX;
  mouseY = event.pageY;
});

function changetab(newtab) {
  tab.value = newtab;
  /*homeleave.value = true;
  youtubeenter.value = true*/
}
</script>

<template>
  <div>
    <div class="blob" :style="{ left: blobleft, top: blobtop }"></div>
    <div class="blur" :style="{ left: blobleft, top: blobtop }"></div>
    <!--  <div class="graph" >
    </div> -->
    <Navigation @tabchange="changetab" />
    <div>
      <div class="main" :class="{ tableave: tab !== 'home', tabenter: tab === 'home'} ">
        <Hero :tab="tab"/>
      </div>
      <div class="main tab-hidden" :class="{ tableave: tab !== 'youtube', tabenter: tab === 'youtube'} ">
        <Youtube :tab="tab"/>
      </div>
    </div>
  </div>
</template>

<style scoped>
.main  {
  position: absolute;
  top: 4rem;
  left: 0rem;
  height: calc(100vh - 4rem);
  width: 100%;
}
/*
.tab-hidden {
  transform: translateX(100vw);
}
*/
.tableave {
  transform: translateX(-100vw);
  animation: tab-leave-animation 500ms ease-in-out;
}

@keyframes tab-leave-animation {
  0% {
    transform: translateX(0vw);
  }
  100% {
    transform: translateX(-100vw);
  }
}
/*
.tabenter {
  transform: translateX(0);
  animation: tab-enter-animation 500ms ease-in-out;
}

@keyframes tab-enter-animation {
  0% {
    transform: translateX(100vw);
  }
  100% {
    transform: translateX(0vw);
  }
}
*/

.blob {
  background-color: white;
  height: 20rem;
  width: 20rem;
  position: fixed;
  left: 50%;
  top: 50%;
  translate: -50% -50%;
  border-radius: 50%;
  background: transparent;
  background: linear-gradient(
    9deg,
    rgba(132, 206, 235, 0.8) 5%,
    rgba(193, 200, 228, 0.8) 30%,
    rgba(136, 96, 208, 0.8) 88%
  );
  animation: rotation 15s infinite linear;
  z-index: -2;
  filter: blur(5.5rem);
}

.blur {
  height: 200rem;
  width: 200rem;
  position: fixed;
  left: 50%;
  top: 50%;
  translate: -50% -50%;
  z-index: -1;
 /* backdrop-filter: blur(5.5rem);*/
}

/*
@media only screen and (min-width: 48rem) {
  .main {
    margin-left: 10rem;
  }
}
*/
.graph {
  position: absolute;
  bottom: 0;
  left: 0;
  height: 100%;
  width: 100%;
  z-index: -1;
  background-image: url(./assets/graph-2.svg);
  background-size: cover;
}

@keyframes rotation {
  from {
    transform: rotate(0deg);
  }
  35% {
    scale: 1 1.3;
  }

  to {
    transform: rotate(359deg);
  }
}
</style>
