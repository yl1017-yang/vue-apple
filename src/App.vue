<template>

  <div class="black-bg" v-if="modalOpen == true">
    <div class="white-bg">
      <h4>모달팝업 타이틀</h4>
      <p>모달팝업 내용입니다.</p>
      <button @click="modalOpen = false">팝업닫기</button>
    </div>
  </div>


  <div class="menu">
    <a v-for="a in menus" :key="a" href="#">{{ a }}</a>
  </div>
  
  <!-- <div v-for="(product,i) in products" :key="i" class="product-auto">
    <h4>{{ product }}</h4>
    <p>{{ price[i] }} 만원</p>
    <span>신고수 : {{ 신고수[i] }}</span>
  </div> -->

  <div>전체 강의는 https://codingapple.com/course/vue-js/ 에서 구독자용 할인 코드 YT123</div>

  <div class="product">
    <div v-for="(oneroom, i) in 원룸들" :key="i">
      <img :src="원룸들[i].image" />
      <h4 @click="modalOpen = true">{{ 원룸들[i].title }}</h4>
      <p>{{ 원룸들[i].price }} 원</p>
    </div>
  </div>
</template>

<script>
import data from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return {
      modalOpen : false, //0, 1로 표현해도 됨 // 리액트는 state임
      price : [60, 80, 100],
      신고수 : [0, 0, 0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      원룸들 : data,
    }
  },

  //함수선언 function
  methods : {
    increase(){
      this.신고수 += 1;
    },
  },

  components: {
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
}
</style>
