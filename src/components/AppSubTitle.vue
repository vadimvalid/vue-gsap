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
  <p class="subtitle">{{ title }}</p>
</template>

<style scoped>
.subtitle {
  font-size: 1.75rem;
  line-height: 1.35;
  text-align: center;
}

@media screen and (max-width: 1200px) {
  .title {
    font-size: 1.25rem;
  }
}

@media screen and (max-width: 768px) {
  .title {
    font-size: 0.875rem;
  }
}
</style>
