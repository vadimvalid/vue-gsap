<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";
import AppHeader from "./components/AppHeader.vue";
const revealUp = ref(true);
const animateImage = () => {
  gsap.fromTo(
    revealUp.value,
    {
      opacity: 0,
      clipPath: "polygon(0% 8%, 0% 7%, 0% 99%,0% 100%)",
      autoAlpha: 0,
      scale: 1.2,
    },
    {
      opacity: 1,
      clipPath: "polygon(0% 0%, 100% 0%, 100% 100%,0% 100%)",
      autoAlpha: 1,
      delay: 0.5,
      scale: 1,
      duration: 3,
      ease: "power4.out",
    }
  );
};

const animateInfo = () => {
  const tl = gsap.timeline();
  tl.fromTo(
    ".revealUp",
    {
      opacity: 0,
      y: 150,
      autoAlpha: 0,
      stagger: {
        each: 0.1,
        from: "top",
        ease: "power2.inOut",
      },
    },
    {
      opacity: 1,
      y: 0,
      autoAlpha: 1,
      delay: 0.5,
      duration: 1,
      ease: "power4.out",
      stagger: {
        each: 0.1,
        from: "top",
        ease: "power2.inOut",
      },
    }
  );
};

onMounted(() => {
  animateImage();
  animateInfo();
});
</script>

<template>
  <app-header />
</template>
