<template>  

  <div class="menu">
    <a v-for="a in menus" :key="a" href="#">{{ a }}</a>
  </div>
  
  <div>전체 강의는 https://codingapple.com/course/vue-js/ 에서 구독자용 할인 코드 YT123</div>
  <div>https://iancoding.tistory.com/232?category=1196039</div>
  <!-- <div v-for="(product,i) in products" :key="i" class="product-auto">
    <h4>{{ product }}</h4>
    <p>{{ price[i] }} 만원</p>
    <span>신고수 : {{ 신고수[i] }}</span>
  </div> -->  
  
  
  <Discount v-if="showDiscount == true" :amount="amount"/>
  <!-- <div class="discount" >
    <h4>지금 결제하면 <span>{{ amount }}</span>% 할인</h4>
  </div> -->

  <button @click="priceSort">가격낮은순 정렬</button>
  <button @click="priceSort2">가격높은순 정렬</button>
  <button @click="priceSort3">가나다순 정렬</button>
  <button @click="sortBack">되돌리기</button>


  <!-- <div class="start" :class="{ end : modalOpen }"> -->
  <transition name="fade">
    <Modal @closeModal="modalOpen = flase" :원룸들="원룸들" :누른거="누른거" :modalOpen="modalOpen" />
  </transition>

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
      showDiscount : true,
      amount : 20,
      오브젝트 : { name : 'kim', age : 20},
      누른거 : 0,
      원룸들오리지널 : [...data], //array/object 데이터의 각각 별개의 사본
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
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
    },
    priceSort(){
      // var array = [3, 5, 2];
      // array.sort(function(a,b){
      //   return a - b
      // });
      // console.log(array);

      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })
    },
    priceSort2(){
      this.원룸들.sort(function(a,b){
        return b.price - a.price
      })
    },
    priceSort3(){
      this.원룸들.sort(function(a,b){
        return a.title.localeCompare(b.title)
      })
    }
  },


  // created(){ //html 생성전
  //   //서버에서 데이터 가져오는 코드 
  // },
  mounted(){ //컴포넌트가 html에 잘 장착된 상태, 서버에게 데이터 요청할 시 필요(ajax)
    // setTimeout(() => {
    //   this.showDiscount = false;
    // }, 2000);

    const timer = setInterval(() => {
      this.amount -= 1;
      if ( this.amount <= 0 ) {
        clearInterval(timer);
      }
    }, 1000);

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


.discount {
  background: #eee;
  padding: 10px;
  margin: 20px;
  color: darkcyan;
  font-size: 25px;
}
.discount span {
  font-size: 40px;
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

/* css fade 애니메이션 */
.start {
  opacity: 0;
  transition: all 1s;
}
.end {
  opacity: 1;
}

/* vue transition fade 애니메이션 */
.fade-leave-from {
  opacity: 1;
  /* transform: translateY(0px); */
}
.fade-leave-active {
  transition: all 0.8s;
}
.fade-leave-to {
  opacity: 0;
  /* transform: translateY(-100%); */
}

.fade-enter-from {
  opacity: 0;
  /* transform: translateY(-100%); */
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
  /* transform: translateY(0px); */
}
</style>
