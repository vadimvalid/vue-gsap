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
</style>
