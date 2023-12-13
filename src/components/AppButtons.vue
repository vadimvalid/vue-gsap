<script setup>
import { defineProps } from "vue";
import AppButton from "./AppButton.vue";

const props = defineProps({
  items: {
    type: Array,
    required: true,
  },
});
</script>

<template>
  <div class="buttons">
    <app-button v-for="item in props.items" :key="item.href" v-bind="item" />
  </div>
</template>

<style scoped>
.buttons {
  display: flex;
  padding: 6px;
  background-color: #f4f2f6;
  border-radius: 13px;
}
</style>
