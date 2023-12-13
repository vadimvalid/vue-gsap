<script setup>
import { defineProps, computed } from "vue";

const props = defineProps({
  title: {
    type: Array,
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
