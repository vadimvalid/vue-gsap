<script setup>
import { ref } from "vue";
import AppLogo from "./AppLogo.vue";
import AppNav from "./AppNav.vue";
import AppButtons from "./AppButtons.vue";

const logoProps = ref({
  href: "/",
  src: "logo.svg",
  alt: "Vite logo",
});

const navItems = ref({
  items: [
    {
      href: "#",
      title: "Продукты",
    },
    {
      href: "#",
      title: "Решения",
    },
    {
      href: "/tafifs",
      title: "Тарифы",
      isDropdown: false,
    },
  ],
});

const navItemsSecond = ref({
  items: [
    {
      href: "#",
      title: "О нас",
    },
    {
      href: "#",
      title: "Документы",
    },
  ],
});

const buttons = ref({
  items: [
    {
      title: "Вход",
    },
    {
      title: "Регистрация",
      isSecondary: true,
    },
  ],
});
</script>

<template>
  <header>
    <div class="container">
      <div class="wrapper">
        <app-logo v-bind="logoProps" />
        <app-nav v-bind="navItems" />
        <app-nav v-bind="navItemsSecond" />
        <app-buttons v-bind="buttons" />
        <div class="lang">
          <ul>
            <li><a href="#">En</a></li>
          </ul>
        </div>
      </div>
    </div>
  </header>
</template>

<style scoped>
.wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.lang a {
  color: #989898;
}
</style>
