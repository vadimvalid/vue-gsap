<script setup>
import { defineProps } from "vue";

const props = defineProps({
  href: {
    type: String,
    required: false,
  },
  title: {
    type: String,
    required: true,
  },
  isDropdown: {
    type: Boolean,
    default: true,
  },
});
</script>

<template>
  <li class="nav-item">
    <a :href="href">{{ title }}</a>
    <svg
      v-if="isDropdown"
      xmlns="http://www.w3.org/2000/svg"
      width="8"
      height="5"
      fill="none"
    >
      <path
        stroke="#222"
        stroke-linecap="round"
        stroke-linejoin="round"
        d="M.667.667 4.001 4 7.334.667"
      />
    </svg>
  </li>
</template>

<style scoped>
.nav-item {
  display: flex;
  align-items: center;
}
.nav-item > a {
  margin-right: 0.5rem;
  color: #222;
}

.nav-item > svg {
  cursor: pointer;
}
</style>
