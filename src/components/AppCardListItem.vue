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
</style>
