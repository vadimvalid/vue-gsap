<script setup>
import { defineProps } from "vue";
import AppNavItem from "./AppNavItem.vue";

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <ul class="nav-menu">
    <app-nav-item v-for="item in props.items" :key="item.href" v-bind="item" />
  </ul>
</template>

<style scoped>
.nav-menu {
  display: flex;
  gap: 2.5rem;
}
</style>
