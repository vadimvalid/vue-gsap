<script setup>
import { onMounted, ref } from "vue";
import gsap from "gsap";
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

const animateHeader = () => {
  const tl = gsap.timeline();
  tl.fromTo(
    ".header",
    {
      opacity: 0,
      y: 100,
    },
    {
      opacity: 1,
      y: 0,
      duration: 1,
      ease: "power1.out",
    }
  );
};

onMounted(() => {
  animateHeader();
});
</script>

<template>
  <header class="header">
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
.header {
  padding: 1.25rem 0;
}

.wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.lang a {
  color: #989898;
}

@media screen and (max-width: 1200px) {
  .wrapper {
    flex-wrap: wrap;
    gap: 1rem;
  }

  .wrapper > .logo {
    flex: 1;
  }

  .wrapper > .logo {
    flex: 1 1 auto;
  }

  .wrapper > .nav-menu {
    flex: 1;
    order: 1;
    flex-basis: 100%;
    padding-left: 0;
  }

  .wrapper > .nav-menu:last-of-type {
    order: 2;
  }
}

@media screen and (max-width: 768px) {
  .lang {
    font-size: 0.875rem;
  }
}
</style>
