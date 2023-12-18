<script setup>
import { computed, defineProps, onMounted, onUnmounted, ref } from "vue";
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

const deg = ref(0);

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
        trigger: ".circle__svg",
        start: "top top",
      },
    })
    .to(".circle__svg", {
      rotation: 180,
      duration: 2,
      ease: "none",
    });
};

onMounted(() => {
  animateCircle();
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});

const handleScroll = () => {
  deg.value = window.scrollY * 0.5;
};

const rotate = computed(() => {
  return {
    transform: `rotate(${deg.value}deg)`,
  };
});
</script>

<template>
  <div class="circle">
    <svg
      class="circle__svg"
      :style="rotate"
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

@media screen and (max-width: 1200px) {
  .circle__svg {
    width: 8rem;
    height: 8rem;
  }
}

@media screen and (max-width: 768px) {
  .circle__svg {
    width: 5rem;
    height: 5rem;
  }
}
</style>
