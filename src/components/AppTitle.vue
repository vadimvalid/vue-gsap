<script setup>
import { defineProps, computed } from "vue";

const props = defineProps({
  title: {
    type: Array,
    required: true,
  },
});

const title = computed(() => props.title.join(" "));
</script>

<template>
  <h1 class="title">{{ title }}</h1>
</template>

<style scoped>
.title {
  font-size: 5rem;
  line-height: 1.1;
  text-align: center;
}
</style>
