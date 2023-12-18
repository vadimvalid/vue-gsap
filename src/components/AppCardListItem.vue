<script setup>
import { defineProps } from "vue";

const props = defineProps({
  title: {
    type: String,
    required: true,
  },
});
</script>

<template>
  <li>{{ title }}</li>
</template>

<style scoped>
li {
  font-size: 1.75rem;
  line-height: 1.35;
  list-style: initial;
}

@media screen and (max-width: 1200px) {
  li {
    font-size: 1rem;
  }
}

@media screen and (max-width: 768px) {
  li {
    font-size: 0.875rem;
  }
}
</style>
