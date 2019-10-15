<template>
  <a href="javascript:void(0)" class="button" @click="addToBasket()">
     Добавить в корзину
  </a>
</template>

<script>
import axios from 'axios'

export default {
  props: {
    id: Number,
  },

  methods: {
    addToBasket() {
     axios
      .post(`http://vue-tests.dev.creonit.ru/api/cart/product/${this.id}`)
      .then(response => (alert('Товар добавлен в корзину')))
      .catch(error => console.log(error));
    }
  }
}
</script>

<style lang="scss">

.button {
  position:relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 80%;
  height: 46px;
  border: 1px solid #ccc;
  font: 700 14px 'Arial', sans-serif;
  color: #333;
  text-decoration: none;
  transition: all .3s;
  border-radius: 7px;
  text-align: center;
  margin: 0 auto;

  &:hover {
    background-color: #07378B;
    border-color: transparent;
    color: #fff;
  }
}

</style>
