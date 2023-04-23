<script setup>
import { ref } from "vue";

const props = defineProps(["tab"]);

const count = ref(0);
</script>

<template>
  <Transition>
    <div v-if="tab === 'home'" class="hero-wrapper">
      <div class="left">
        <div class="name" :class="{ nameamimation: tab === 'home' }">
          <h1>S</h1>
          <h1>M</h1>
          <h1>O</h1>
          <h1>K</h1>
          <h1>L</h1>
          <h1>M</h1>
        </div>
        <div class="icon-row">
          <a class="icon-wrapper" href="https://www.youtube.com/smoklm"
            ><img class="icon" src="../assets/youtube-svgrepo-com.svg" alt=""
          /></a>
          <a class="icon-wrapper" href="https://www.youtube.com/smoklm"
            ><img class="icon" src="../assets/linkedin-svgrepo-com.svg" alt=""
          /></a>
          <a class="icon-wrapper" href="https://www.youtube.com/smoklm"
            ><img class="icon" src="../assets/instagram-svgrepo-com.svg" alt=""
          /></a>
          <a class="icon-wrapper" href="https://www.youtube.com/smoklm"
            ><img class="icon" src="../assets/twitter-svgrepo-com.svg" alt=""
          /></a>
        </div>
      </div>
      <div class="video">
        <iframe
          src="https://www.youtube.com/embed/jD4IISOja6Q"
          title="YouTube video player"
          frameborder="0"
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
          allowfullscreen
        ></iframe>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: all 0.5s ease-out;
}
.read-the-docs {
  color: #888;
}
.hero-wrapper {
  height: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 3rem;
}

.left {
  display: flex;
  flex-direction: column;
  margin-bottom: 2rem;
}

.name {
  letter-spacing: 0.2rem;
  margin-bottom: 1.5rem;
  display: flex;
}

.nameamimation h1 {
  animation: icon-load 500ms ease-out;
  animation-fill-mode: forwards;
  opacity: 0%;
}

.nameamimation h1:nth-child(1) {
  animation-delay: 1.6s;
}
.nameamimation h1:nth-child(2) {
  animation-delay: 1.4s;
}
.nameamimation h1:nth-child(3) {
  animation-delay: 1.2s;
}
.nameamimation h1:nth-child(4) {
  animation-delay: 1s;
}
.nameamimation h1:nth-child(5) {
  animation-delay: 0.8s;
}
.nameamimation h1:nth-child(6) {
  animation-delay: 0.6s;
}

.icon-row {
  display: flex;
  justify-content: flex-end;
  gap: 1rem;
  margin-right: 0.5rem;
}

.icon-row a {
  animation: icon-load 500ms ease-out;
  animation-fill-mode: forwards;
  opacity: 0%;
}

.icon-row a:nth-child(1) {
  animation-delay: 1.2s;
}
.icon-row a:nth-child(2) {
  animation-delay: 1s;
}
.icon-row a:nth-child(3) {
  animation-delay: 0.8s;
}
.icon-row a:nth-child(4) {
  animation-delay: 0.6s;
}

.icon-wrapper:hover {
  scale: 1.2;
  transition: all ease-out 150ms;
}

@media only screen and (max-width: 64rem) {
  .hero-wrapper {
    flex-direction: column;
  }
  .icon-row {
    justify-content: center;
    margin-right: 0;
  }
}

.video iframe {
  aspect-ratio: 16 / 9;
  width: min(40rem, calc(100vw - 5rem));
  animation: icon-load 800ms ease-out;
  animation-delay: 0.6s;
  animation-fill-mode: forwards;
  opacity: 0%;
}

@keyframes icon-load {
  0% {
    opacity: 0%;
    transform: translateY(50px);
  }

  100% {
    opacity: 100%;
    transform: translateY(0);
  }
}
</style>
