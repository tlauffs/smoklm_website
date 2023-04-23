<script setup>
import { ref } from "vue";

defineProps({
  msg: String,
});

const count = ref(0);

</script>

<template>
  <div class="nav-bar">
    <button @click="$emit('tabchange', 'home')" class="btn-link btn-nav"><p>Home</p></button>
    <button @click="$emit('tabchange', 'youtube')" class="btn-link btn-nav"><p>Youtube</p></button>
    <button @click="$emit('tabchange', 'discounts')" class="btn-link btn-nav"><p>Discounts</p></button>
    <button @click="$emit('tabchange', 'contact')" class="btn-link btn-nav"><p>Contact</p></button>
  </div>
</template>
<style>

.nav-bar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 4rem;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  gap: 2rem;
  background-color: #0f0f0f;
}

.btn-nav {
  overflow: hidden;
  margin: 0 1rem;
}

.btn-nav p {
  margin-top: 1.2rem;
}

.btn-nav:after {
  content: "";
  display: inline-block;
  background-color: var(--highlight-color);
  width: 100%;
  height: 0.2rem;
  transform: translateX(-120%);
}
.btn-nav:hover::after {
  transform: translateX(0);
  transition: all ease-out 200ms;
}
</style>
