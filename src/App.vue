<template>
  <div class="app">
    <div class="app__container">
      <tabs 
        :catalog=catalog
        @changeTab="changeTab">
        
      </tabs>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Tabs from './Tabs.vue'

export default {
mounted() {
    axios
      .get('http://vue-tests.dev.creonit.ru/api/catalog/shiny')
      .then(response => (this.catalog.shiny.value = response));

    axios
      .get('http://vue-tests.dev.creonit.ru/api/catalog/diski')
      .then(response => (this.catalog.diski.value = response));  
  },

  data () {
    return {
      catalog: {
        shiny: {
          name: 'Шины',
          active: true,
          value: null,
        },
        diski: {
          name: 'Диски',
          active: false,
          value: null,
        }
      }
    }
  },

  methods: {
    changeTab(ind) {
      for (let key in this.catalog) {
        this.catalog[key].active = false;
      }

      this.catalog[ind].active = true;
    }
  },

  components: {
    Tabs: Tabs,
  }
}
</script>

<style lang="scss">

html,
body {
  margin: 0;
  padding: 0;
}

.app {
  
  &__container {
    max-width: 960px;
    margin: 0 auto;
    padding: 0 10px;
  }
}
</style>
