<script setup>
import { ref, watch } from "vue";

const props = defineProps(["tab"]);

const videoList = ref([
  "https://www.youtube.com/embed/PvztJPAb7jM",
  "https://www.youtube.com/embed/ZXBa-5wwcfc",
  "https://www.youtube.com/embed/dsclgPv32fU",
  "https://www.youtube.com/embed/X8OBHQUQoTM",
  "https://www.youtube.com/embed/jD4IISOja6Q",
  "https://www.youtube.com/embed/NEMsPKkchJ0",
]);
</script>

<template>
  <Transition>
    <div v-if="tab === 'youtube'" class="youtube-wrapper">
      <div class="video-grid" :class="{ gridanimation: tab === 'youtube' }">
        <div class="video" v-for="video in videoList">
          <iframe
            class="video-iframe"
            :src="video"
            title="YouTube video player"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
            allowfullscreen
          ></iframe>
        </div>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: all 0.5s ease-out;
}

.gridanimation div {
  opacity: 0%;
}

@keyframes video-load {
  0% {
    transform: translateX(400px);
    opacity: 0%;
  }
  100% {
    transform: translateX(0px);
    opacity: 100%;
  }
}

@keyframes video-load-r {
  0% {
    transform: translateX(-400px);
    opacity: 0%;
  }
  100% {
    transform: translateX(0px);
    opacity: 100%;
  }
}

@keyframes video-load-y {
  0% {
    transform: translateY(100px);
    opacity: 0%;
  }
  100% {
    transform: translateY(0px);
    opacity: 100%;
  }
}
.gridanimation div:nth-child(1) {
  animation: video-load-r 500ms ease-out;
  animation-fill-mode: forwards;
  animation-delay: 0.5s;
}
.gridanimation div:nth-child(2) {
  animation: video-load 500ms ease-out;
  animation-fill-mode: forwards;
  animation-delay: 0.55s;
}
.gridanimation div:nth-child(3) {
  animation: video-load 500ms ease-out;
  animation-fill-mode: forwards;
  animation-delay: 0.58s;
}
.gridanimation div:nth-child(4) {
  animation: video-load 500ms ease-out;
  animation-fill-mode: forwards;
  animation-delay: 0.55s;
}
.gridanimation div:nth-child(5) {
  animation: video-load 500ms ease-out;
  animation-fill-mode: forwards;
  animation-delay: 0.5s;
}
.gridanimation div:nth-child(6) {
  animation: video-load-y 500ms ease-out;
  animation-delay: 0.5s;
  animation-fill-mode: forwards;
}

.youtube-wrapper {
  display: flex;
  height: 100%;
  justify-content: center;
  align-items: center;
}
.video-grid {
  display: grid;
  width: min(60rem, calc(100% - 4rem));
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(4, 1fr);
  gap: 1rem;
}
.video {
}

.video:nth-child(1) {
  grid-column: 1 / 3;
  grid-row: 1 / 3;
}

.video:nth-child(5) {
  grid-column: 2 / 4;
  grid-row: 3 / 5;
}

.video-iframe {
  width: 100%;
  height: 100%;
}
</style>
