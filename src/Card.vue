<template>
  <div class="product">    
    <div>  <!-- v-for="(a,i) in 원룸들" :key="i" @click="modalOpen = true; 누른거 = i" -->
      <img :src="원룸.image" />
      <h4 @click="send">{{ 원룸.title }}</h4> 
      <!-- <p>{{ 원룸들[i].content }}</p> -->
      <p>{{ 원룸.content }}</p>
      <p>{{ 원룸.price }} 원</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  props : {
    원룸 : Object,
  },
  methods : {
     send() {
      this.$emit('openModal', this.원룸.id)
    },
  }
}
</script>

<style>
.product-auto {
  background: #eee;
  margin: 0 50px;
  padding: 10px;
  border-radius: 10px;
  border-bottom: 2px solid #fff;
}
.product {
  margin: 50px;
}
.product > div {
  padding: 30px 0;
  border-top: 1px solid #ddd;
}
.product h4 {
  font-size: 20px;
  font-weight: bold;
  cursor: pointer;
}
.product img {
  width: 100%;
  margin-top: 40px;
}
</style>