<template>
  <div class="products">
    <img :src="item.image" alt="" />
    <h4 @click="$emit('openModal', item.id)">{{ item.title }}</h4>
    <p>{{ item.price }}원</p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    item: Array,
    selectNum: Number,
    isOpen: Boolean
  }
}
</script>

<style>
.products {
  text-align: center;
  margin-top: 50px;
}
</style>
