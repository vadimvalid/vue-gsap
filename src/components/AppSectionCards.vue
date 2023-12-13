<script setup>
import { ref, defineProps, onMounted } from "vue";
import AppCard from "./AppCard.vue";
import AppCircleText from "./AppCircleText.vue";
import gsap from "gsap";
import ScrollTrigger from "gsap/ScrollTrigger";
gsap.registerPlugin(ScrollTrigger);

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
});

const circleProps = ref({
  src: "arrow-down.svg",
  title: "ВЫБРАТЬ ПРОДУКТ ВЫБРАТЬ ПРОДУКТ",
});

const animateCards = () => {
  const tl = gsap.timeline();
  tl.fromTo(
    ".up",
    {
      opacity: 0,
      y: 100,
      stagger: {
        each: 0.2,
        from: "top",
        ease: "power2.inOut",
      },
    },
    {
      opacity: 1,
      y: 0,
      duration: 1,
      delay: 0.5,
      ease: "power1.out",
      stagger: {
        each: 0.2,
        from: "top",
        ease: "power2.inOut",
      },
    }
  );
};

const animateCardsScroll = () => {
  const cards = gsap.utils.toArray(".card");
  cards.forEach((section, i) => {
    const tl = gsap
      .timeline({
        scrollTrigger: {
          trigger: section,
          start: "top 5%",
          pin: true,
          end: "+=" + 100 * (cards.length - 1) + "%",
          scrub: true,
        },
        onComplete: () => {
          ScrollTrigger.refresh();
        },
      })
      .fromTo(
        section,
        {
          opacity: 1,
          y: 100,
        },
        {
          opacity: 0,
          y: 0,
          scaleY: 0.9,
          scaleX: 0.9,
          duration: 1,
          ease: "power1.out",
        }
      );
  });
};

onMounted(() => {
  animateCards();
  animateCardsScroll();
});
</script>

<template>
  <section id="cards">
    <div class="container">
      <div class="wrapper">
        <div class="svg-shape">
          <app-circle-text v-bind="circleProps" class="up" />
        </div>
        <div class="wrapper__cards">
          <app-card
            v-for="item in items"
            :key="item.cardNumber"
            v-bind="item"
            class="up"
          />
          <div class="empty"></div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.wrapper {
  position: relative;
}

.wrapper__cards {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
}

.svg-shape {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 1;
}

.empty {
  width: 100%;
  height: 10vh;
}
</style>
