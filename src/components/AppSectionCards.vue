<script setup>
import { ref, defineProps } from "vue";
import AppCard from "./AppCard.vue";
import AppCircleText from "./AppCircleText.vue";

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
});

const circleProps = ref({
  src: "arrow-down.svg",
  title: "ПРОДУКТ ВЫБРАТЬ ПРОДУКТ ВЫБРАТЬ",
});
</script>

<template>
  <section>
    <div class="container">
      <div class="wrapper">
        <div class="svg-shape"><app-circle-text v-bind="circleProps" /></div>
        <app-card v-for="item in items" :key="item.cardNumber" v-bind="item" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.wrapper {
  position: relative;
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
</style>
