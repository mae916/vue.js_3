<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>

  <h4 class="Banner">지금 결제하면 30% 할인</h4>
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
export default {
  data() {
    return {
      object: {
        name: 'Kim',
        age: 20
      },
      isOpen: false,
      selectNum: 0,
      menus: ['Home', 'shop', 'About'],
      items
    }
  },
  components: {
    Modal,
    Card
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

.Banner {
  background: #f0f0f0;
  padding: 40px;
  text-align: center;
  border-radius: 5px;
}

.products {
  text-align: center;
  margin-top: 50px;
}
img {
  width: 100%;
}
</style>
