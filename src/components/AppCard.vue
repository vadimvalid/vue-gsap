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
    type: String,
    required: true,
  },
});

const getImageUrl = () => {
  return new URL(`../assets/${props.cardImage}`, import.meta.url);
};
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
      <img :src="getImageUrl()" alt="Card image" />
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
  position: relative;
  flex: 0 1 40%;
  height: 100%;
  background-color: #fff;
  border-radius: 30px;
  aspect-ratio: 1/1;
  background: linear-gradient(327.9deg, #1a005c 19.8%, #6d38f5 100%);
}

.image > img {
  position: absolute;
  bottom: 2.5rem;
  right: 0;
  width: 65%;
  height: auto;
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

@media screen and (max-width: 1200px) {
  .card {
    gap: 3rem;
    padding: 2.5rem;
  }

  .content {
    flex: 0 1 70%;
    gap: 1rem;
  }

  .image {
    flex: 0 1 30%;
  }

  .image > img {
    bottom: 1.5rem;
  }

  .card__number {
    gap: 0.5rem;
    margin-bottom: 1.25rem;
    font-size: 1rem;
  }

  .card__title {
    font-size: 1.25rem;
  }

  .card__subtitle {
    font-size: 1.25rem;
  }

  .card__list {
    gap: 0.5rem;
  }
}

@media screen and (max-width: 768px) {
  .card {
    flex-direction: column;
    gap: 2rem;
    padding: 1.5rem;
  }

  .content {
    flex: none;
    gap: 1rem;
  }

  .image {
    flex: none;
    max-height: 18.75rem;
  }

  .image > img {
    bottom: 1rem;
    width: 50%;
  }

  .card__number {
    margin-bottom: 1rem;
    font-size: 0.875rem;
  }

  .card__title {
    font-size: 1.25rem;
  }

  .card__subtitle {
    font-size: 1rem;
  }

  .card__list {
    gap: 0.25rem;
  }
}
</style>
