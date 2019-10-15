<template>
  <div class="card">
      <img class="card__img" :src="image" :alt="title">
      <div class="card__wrap">
        <div class="card__title">{{ title }}</div>
        <div class="card__price-block">
          <span class="card__price">{{ price }}</span>
          <span class="card__price-currency">руб.</span>
        </div>
        <div class="card__category">Категория: {{ category.title }}</div>
        <app-button :id="id"></app-button>
      </div>
  </div>
</template>

<script>
import AppButton from './AppButton.vue'

export default {
  props: {
    id: Number,
    title: String,
    price: Number,
    image: String,
    category: Object,
  },

  components: {
    AppButton: AppButton,
  }
}
</script>

<style lang="scss">

.card {
  width: 100%;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 0 20px 5px #dedede;

  &__img {
    width: 100%;
  }

  &__wrap {
    padding: 20px;
  }
  
  &__title,
  &__price {
    font: 700 22px 'Arial', sans-serif;
    color: #333;
    margin-bottom: 10px;
  }

  &__price-block {
    margin-bottom: 10px;
  }

  &__price {
    font: 400 22px 'Arial', sans-serif;
  }

  &__price-currency {
    font: 400 14px 'Arial', sans-serif;
  }

  &__category {
    font: 200 14px 'Arial', sans-serif;
    color: #888;
    margin-bottom: 15px;
  }
}
</style>
