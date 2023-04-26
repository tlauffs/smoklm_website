<script setup>
import { ref, watch } from "vue";

const props = defineProps(["tab"]);

const discountList = ref([
  {
    name: "Hivemapper",
    code: "SMOK10",
    link: "https://shop.hivemapper.com/products/hivemapper-dashcam-pi?ref=SMOKLM",
  },
  {
    name: "DIMO",
    code: "SMOKLM",
    link: "https://shop.dimo.zone/products/dimo-data-device?ref=o0HHHKSC",
  },
  {
    name: "Fry Foundation",
    code: "SMOKLM",
    link: "https://www.fryfoundation.com/?ref=urgo3xam",
  },
]);
</script>

<template>
  <Transition>
    <div v-if="tab === 'discounts'" class="discount-wrapper">
      <div v-for="discont in discountList" class="discount">
        <h2>{{ discont.name }}</h2>
        <p class="code">Code: {{ discont.code }}</p>
      </div>
    </div>
  </Transition>
</template>

<style scoped>
.v-enter-active,
.v-leave-active {
  transition: all 0.5s ease-out;
}

p,
h2 {
  mix-blend-mode: difference;
}
.discount-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 2rem;
  gap: 1.5rem;
}

.discount {
  width: min(90%, 35rem);
  padding: 0.7rem 1rem;
  background-color: #0f0f0f;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  border-radius: 10px;
  /*
  background: rgba(136, 96, 208, 1);
   background: linear-gradient(
    90deg,
    rgba(136, 96, 208, 1) 5%,
    rgba(193, 200, 228, 1) 70%,
    rgba(132, 206, 235, 1)88%
  );
  */
}

.discount h2 {
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.discount:nth-child(even) {
  text-align: right;
}

.discount::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: white;
  border-radius:  10px;
  transform: translateX(100%);
  transition: all .3s ease-in;
}

.discount:nth-child(even)::before {
  transform: translateX(-100%);
}

.discount:hover::before {
    transform: translateX(0);
}

.discount:hover .code {
    /*font-size: larger; */
}
</style>
