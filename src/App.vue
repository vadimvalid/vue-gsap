<script setup>
import { onMounted, ref } from "vue";
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

const parallaxSection = () => {
  gsap.to("#titles", {
    scrollTrigger: {
      trigger: "#titles",
      start: "top top",
      end: "bottom top",
      scrub: true,
    },
    y: "50%",
    opacity: 0,
  });
};

onMounted(() => {
  parallaxSection();
});
</script>

<template>
  <app-header />
  <main class="main">
    <app-section-title />
    <app-section-cards v-bind="cardProps" />
  </main>
</template>
