<script setup>
import { defineProps, onMounted } from "vue";
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  src: {
    type: String,
    required: true,
  },
});

const getImageUrl = () => {
  return new URL(`../assets/${props.src}`, import.meta.url);
};

const animateCircle = () => {
  const tl = gsap
    .timeline({
      scrollTrigger: {
        trigger: "#cards",
        start: "top top",
        end: "+=10000",
      },
    })
    .to(".circle__svg", {
      rotation: 360 * 5,
      duration: 1,
      ease: "none",
    });
};

onMounted(() => {
  animateCircle();
});
</script>

<template>
  <div class="circle">
    <svg
      class="circle__svg"
      viewBox="0 0 160 160"
      xmlns="http://www.w3.org/2000/svg"
    >
      <path
        fill="none"
        id="circlePath"
        d="
      M 30, 80
      a 40,40 0 1,1 100,0
      40,40 0 1,1 -100,0
    "
      />
      <text>
        <textPath href="#circlePath">{{ title }}</textPath>
      </text>
    </svg>
    <img :src="getImageUrl()" alt="arrow down" class="circle__arrow" />
  </div>
</template>

<style scoped>
.circle {
  position: relative;
}

.circle__svg {
  border-radius: 50%;
  background: #dafe69;
  width: 10rem;
  height: 10rem;
}

.circle__arrow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
}
</style>
