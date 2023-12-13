<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";
import AppTitle from "./AppTitle.vue";
import AppSubTitle from "./AppSubTitle.vue";

const titleProps = ref({
  title: [
    "Платформа защищенного ",
    "видеохостинга ",
    "онлайн-трансляций ",
    "и монетизации видеоконтента",
  ],
});

const subTitleProps = ref({
  title:
    "Для защиты ваших видео от пиратства, онлайн-трансляций по всему миру и заработка на видеоконтенте",
});

const animateTitles = () => {
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

onMounted(() => {
  animateTitles();
});
</script>

<template>
  <section id="titles">
    <div class="container">
      <div class="wrapper">
        <app-title v-bind="titleProps" class="up" />
        <app-sub-title v-bind="subTitleProps" class="up" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  padding: 12.5rem 0;
}
</style>
