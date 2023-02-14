<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <Discount :dcPercent="dcPercent" />

  <div class="sort-btn">
    <v-btn elevation="2" outlined text></v-btn>
    <button @click="latest">최신순(기본순)</button>
    <button @click="lowPrice">낮은 가격순</button>
    <button @click="highPrice">높은 가격순</button>
    <button @click="titleSort">이름순</button>
  </div>
  <Modal
    @closeModal="isOpen = false"
    :items="items"
    :selectNum="selectNum"
    :isOpen="isOpen"
  />

  <Card
    @openModal=";(isOpen = true), (selectNum = $event)"
    :item="items[i]"
    v-for="(item, i) in items"
    :key="i"
  />
</template>

<script>
import items from './assets/data'
import Modal from './components/modal.vue'
import Card from './components/card.vue'
import Discount from './components/discount.vue'
export default {
  data() {
    return {
      originalItems: [...items],
      object: {
        name: 'Kim',
        age: 20
      },
      isOpen: false,
      selectNum: 0,
      menus: ['Home', 'shop', 'About'],
      items,
      dcPercent: 30
    }
  },
  components: {
    Modal,
    Card,
    Discount
  },
  mounted() {
    setInterval(() => {
      if (this.dcPercent >= 1) {
        this.dcPercent--
      }
    }, 1000)
  },
  methods: {
    latest() {
      this.items = [...this.originalItems]
    },
    lowPrice() {
      this.items.sort((a, b) => {
        return a.price - b.price
      })
    },
    highPrice() {
      this.items.sort((a, b) => {
        return b.price - a.price
      })
    },
    titleSort() {
      this.items.sort((a, b) => {
        if (a.title.toUpperCase() > b.title.toUpperCase()) {
          return 1
        } else {
          return -1
        }
      })
    }
  }
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}

img {
  width: 100%;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
  text-align: center;
}
.menu a {
  color: white;
  padding: 10px;
}
.sort-btn {
  display: flex;
  justify-content: space-evenly;
  width: 40%;
}
</style>
