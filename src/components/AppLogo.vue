<script setup>
import { defineProps } from "vue";

const props = defineProps({
  href: {
    type: String,
    required: true,
  },
  src: {
    type: String,
    required: true,
  },
  alt: {
    type: String,
    required: true,
  },
});

const getImageUrl = () => {
  return new URL(`../assets/${props.src}`, import.meta.url);
};
</script>

<template>
  <a :href="href" class="logo">
    <img :src="getImageUrl()" :alt="alt" />
  </a>
</template>

<style scoped>
.logo {
  display: flex;
  width: 11.625rem;
}
</style>
