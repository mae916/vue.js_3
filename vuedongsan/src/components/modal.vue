<template>
  <transition name="fade">
    <div v-if="isOpen == true" class="black-bg">
      <div class="white-bg">
        <i @click="$emit('closeModal')" class="xi-close xi-x"></i>
        <img :src="items[selectNum].image" alt="" />
        <h4>{{ items[selectNum].title }}</h4>
        <p>{{ items[selectNum].content }}</p>
        <input v-model="month" />
        <p>{{ month }}개월 선택함 : {{ items[selectNum].price * month }}원</p>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'Modal',
  data() {
    return {
      month: '3'
    }
  },
  beforeUpdate() {
    if (this.month === 2) {
      alert('3개월 이상 입력해주세요.')
    }
  },
  // watch: {
  //   month(before, after) {
  //     if (isNaN(before) === true) {
  //       alert('숫자를 입력해 주세요')
  //       this.month = 1
  //       return false
  //     }
  //     if (before > 12) {
  //       alert('12 이하로 입력해 주세요')
  //       this.month = 1
  //       return false
  //     }
  //   }
  // },
  props: {
    items: Array,
    selectNum: Number,
    isOpen: Boolean
  }
}
</script>

<style>
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
  top: 0;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
  margin-top: 170px;
}
.xi-close {
  display: block;
  text-align: end;
  margin-bottom: 20px;
}
.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}

.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
</style>
