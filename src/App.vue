<template>  

  <div class="menu">
    <a v-for="a in menus" :key="a" href="#">{{ a }}</a>
  </div>
  
  <div>전체 강의는 https://codingapple.com/course/vue-js/ 에서 구독자용 할인 코드 YT123</div>
  <!-- <div v-for="(product,i) in products" :key="i" class="product-auto">
    <h4>{{ product }}</h4>
    <p>{{ price[i] }} 만원</p>
    <span>신고수 : {{ 신고수[i] }}</span>
  </div> -->  
  
  
  
  <!-- 자식 컴퍼넌트 v-bild: 동일 -->
  <Discount />

  <Modal @closeModal="modalOpen = flase" :원룸들="원룸들" :누른거="누른거" :modalOpen="modalOpen" />

  <Card @openModal="modalOpen = true; 누른거 = $event" :원룸="원룸들[i]" v-for="(작명,i) in 원룸들" :key="작명" />
  <!-- <Card :원룸="원룸들[0]" /> 누른거 = i 사용해도 동일한 효과 나옴 -->


  <!-- <div class="product">
    <div v-for="(a,i) in 원룸들" :key="i" @click="modalOpen = true; 누른거 = i ">
      <img :src="a.image" />
      <h4>{{ a.title }}</h4>
      <p>{{ 원룸들[i].content }}</p>
      <p>{{ 원룸들[i].price }} 원</p>
    </div>
  </div> -->

</template>

<script>
import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data(){
    return {
      오브젝트 : { name : 'kim', age : 20},
      누른거 : 0,
      원룸들 : data,
      modalOpen : false, //0, 1로 표현해도 됨 // 리액트는 state임
      menus : ['Home', 'Shop', 'About'],
      //price : [60, 80, 100],
      //신고수 : [0, 0, 0],
      //products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
    }
  },

  //함수선언 function과 동일기능
  methods : {
    increase(){
      this.신고수 += 1;
    },
   
  },

  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  border: 0;
  list-style: none;
  text-decoration: none;
  font-family: 맑은고딕, Helvetica, Arial, sans-serif;
}
div {
  box-sizing: border-box;
}

#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #222;
}

.menu {
  background: darkcyan;
  padding: 30px;
  margin-bottom: 50px;
  border-radius: 0 0 10px 10px;
}
.menu a {
  font-size: 20px;
  color:#fff;
  padding:0 30px;
}

</style>
