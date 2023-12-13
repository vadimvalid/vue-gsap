<script setup>
import { ref, defineProps } from "vue";
import AppCard from "./AppCard.vue";

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <section>
    <div class="container">
      <div class="wrapper">
        <app-card v-for="item in items" :key="item.cardNumber" v-bind="item" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.wrapper {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
}
</style>
