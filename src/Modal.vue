<template>
  <div class="black-bg" v-if="modalOpen == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>
      <p>{{ 원룸들[누른거].price }} 원</p>
      <button @click="sendclose">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  props : {
    원룸들 : Array, 
    누른거 : Number,
    modalOpen : Boolean,
  },
  methods : {
    sendclose() {
      this.$emit('closeModal')
    },
  }
}
</script>

<style>
/* 모달팝업 */
.black-bg {
  position: fixed;
  width: 100%; 
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(0,0,0,0.5);
  padding: 40px;
}
.black-bg img {
  width: 100%;
}
.white-bg {
  width: 100%;
  background: #fff;
  border-radius: 10px;
  padding: 40px;
}
.white-bg button {
  background: darkgreen;
  padding: 10px 50px;
  color: #fff;
  cursor: pointer;
}
</style>