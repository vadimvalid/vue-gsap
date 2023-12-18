<script setup>
import { defineProps } from "vue";

const props = defineProps({
  type: {
    type: String,
    required: false,
    default: "button",
  },
  title: {
    type: String,
    required: true,
  },
  isSecondary: {
    type: Boolean,
    default: false,
  },
});
</script>

<template>
  <button
    :type="type"
    class="button"
    :class="isSecondary && 'button--secondary'"
  >
    {{ title }}
  </button>
</template>

<style scoped>
.button {
  all: unset;
  display: block;
  padding: 0.875rem 1.5rem;
  font-weight: 500;
  background-color: #f4f2f6;
  border-radius: 10px;
  cursor: pointer;
}

.button--secondary {
  background-color: #6d38f5;
  color: #fff;
}

@media screen and (max-width: 768px) {
  .button {
    padding: 0.5rem 1rem;
    font-size: 0.875rem;
  }
}
</style>
