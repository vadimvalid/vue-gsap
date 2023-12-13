<script setup>
import { defineProps, computed } from "vue";
import AppCardListItem from "./AppCardListItem.vue";

const props = defineProps({
  cardNumber: {
    type: String,
    required: true,
  },
  cardName: {
    type: String,
    required: true,
  },
  cardTitle: {
    type: String,
    required: true,
  },
  cardSubTitle: {
    type: String,
    required: false,
  },
  cardListItems: {
    type: Array,
    required: false,
  },
  cardImage: {
    type: Object,
    required: true,
  },
});

const title = computed(() => props.title.join(" "));
</script>

<template>
  <article class="card">
    <div class="content">
      <p class="card__number">
        <span>{{ cardNumber }}</span
        >{{ cardName }}
      </p>
      <h2 class="card__title">{{ cardTitle }}</h2>
      <p class="card__subtitle" v-if="cardSubTitle">{{ cardSubTitle }}</p>
      <ul class="card__list">
        <app-card-list-item
          v-for="item in cardListItems"
          :key="item.title"
          v-bind="item"
        />
      </ul>
    </div>
    <div class="image">
      <!-- <img v-bind="cardImage" /> -->
    </div>
  </article>
</template>

<style scoped>
.card {
  display: flex;
  gap: 7.5rem;
  padding: 5rem;
  background-color: #222;
  border-radius: 13px;
  color: #fff;
}

.content {
  flex: 0 1 60%;
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
}

.image {
  flex: 0 1 40%;
  height: 100%;
  position: relative;
  background-color: #fff;
  border-radius: 30px;
  aspect-ratio: 1/1;
}

.image img {
  height: 100%;
}

.card__number {
  display: flex;
  align-items: center;
  gap: 0.875rem;
  margin-bottom: 1.75rem;
  font-size: 1.25rem;
  color: #dafe69;
}

.card__number span {
  font-style: italic;
}

.card__title {
  font-size: 3.125rem;
  line-height: 1.2;
}

.card__subtitle {
  font-size: 1.75rem;
  line-height: 1.35;
}

.card__list {
  display: flex;
  flex-direction: column;
  gap: 0.875rem;
}
</style>
