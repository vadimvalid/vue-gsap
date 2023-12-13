<script setup>
import { ref } from "vue";
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
</script>

<template>
  <section>
    <div class="container">
      <div class="wrapper">
        <app-title v-bind="titleProps" />
        <app-sub-title v-bind="subTitleProps" />
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
