<template>
  <h4 class="Banner">지금 결제하면 {{ dcPercent }}% 할인</h4>
</template>

<script>
export default {
  name: 'Discount',
  mounted() {
    setTimeout(() => {}, 2000)
  },
  props: {
    dcPercent: Number
  }
}
</script>

<style>
.Banner {
  background: #f0f0f0;
  padding: 40px;
  text-align: center;
  border-radius: 5px;
}
</style>
