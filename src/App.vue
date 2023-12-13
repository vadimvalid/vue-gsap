<script setup>
import { ref, onMounted } from "vue";
import gsap from "gsap";
import AppHeader from "./components/AppHeader.vue";
import AppSectionTitle from "./components/AppSectionTitle.vue";
import AppSectionCards from "./components/AppSectionCards.vue";

const cardProps = ref({
  items: [
    {
      cardNumber: "01",
      cardName: "Видеохостинг",
      cardTitle:
        "Видеохостинг с многоуровневой защитой контента и настройками приватности",
      cardListItems: [
        {
          title: "Управляйте доступом к видео с защитой от пиратства",
        },
        {
          title: "Настраивайте опции и внешний вид плеера",
        },
        {
          title: "Открытое REST API для интеграции",
        },
      ],
      cardImage: {
        src: "https://images.unsplash.com/photo-1605379399642-870262d3d051?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80",
      },
    },
    {
      cardNumber: "02",
      cardName: "Трансляции",
      cardTitle: "Транслируйте видео для тысяч зрителей со всего мира",
      cardListItems: [
        {
          title: "Проводите открытые или закрытые трансляции",
        },
        {
          title: "Монетизируйте контент с помощью платного доступа",
        },
        {
          title: "Вещайте по расписанию автовебинары или поток с ip камеры",
        },
      ],
      cardImage: {
        src: "https://images.unsplash.com/photo-1605379399642-870262d3d051?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80",
      },
    },
    {
      cardNumber: "03",
      cardName: "Монетизация",
      cardTitle: "Система продажи видео-контента",
      cardSubTitle:
        "Прием оплаты в плеере. Для монетизации видеоуроков, вебинаров, трансляций и любого авторского видеоконтента.",
      cardImage: {
        src: "https://images.unsplash.com/photo-1605379399642-870262d3d051?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80",
      },
    },
  ],
});

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
  <main>
    <app-section-title />
    <app-section-cards v-bind="cardProps" />
  </main>
</template>
