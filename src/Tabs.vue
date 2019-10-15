<template>
  <div class="tabs">
    <div class="tabs__header">
       <div class="tabs__item" v-for="(item, ind) in catalog">
          <a href="javascript:void(0)" class="tabs__link" :class="activeTabClass(item.active)" @click="changeTab(ind)" ref="tabLinks">   {{ item.name }} 
          </a>
       </div>
    </div>
    <div class="tabs__content" :class="activeContentClass(item.active)" v-for="item in catalog">
      <div v-for="card in item.value.data.items" class="tabs__col">
        <card :id=card.id
              :title=card.title
              :price=card.price
              :image=card.image_preview
              :category=card.category>
        </card>
      </div>
    </div>
  </div>
</template>

<script>
import Card from './Card.vue'

export default {
  props: {
    catalog: Object,
  },
 
  data () {
    return {

    }
  },

  methods: {
    activeTabClass(active) {
      return {
        'tabs__link_active': active === true,
      } 
    },

    activeContentClass(active) {
      return {
        'tabs__content_active': active === true,
      } 
    },

    changeTab(ind) { 
      this.$emit('changeTab', ind);
    }
  },
  components: {
    Card: Card,
  }
}
</script>

<style lang="scss">
.tabs {
    height: 60px;
    border-bottom: 1px solid #ddd;

  &__header {
    display: flex;
    height: 100%;
    margin-bottom: 40px;
  }

  &__item {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100px;
    height: 100%;
  }

  &__link {
    text-decoration: none;
    font: 200 14px Arial, sans-serif;
    color: #333;

    &:hover {
      color: #00d1b2;
    }

    &_active {
      color: #00d1b2;
      pointer-events: none;
    }
  }

  &__content {
    display: none;
    justify-content: space-between;
    margin: 0 -20px;

    &_active {
      display: flex;
    }
  }

  &__col {
    width: calc(33% - 20px);
    margin: 20px;
  }
}
</style>
