<template>
  <div class="menu">
    <a v-for="a in menus" :key="a" href="#">{{ a }}</a>
  </div>
  
  <div v-for="(product,i) in products" :key="i">
    <h4>{{ product }}</h4>
    <p>{{ price1 }} 만원</p>
  </div>

  <div>https://www.youtube.com/watch?v=UyESqYSb0gY</div>
  <div>
    <h4>{{ products[0] }}</h4>
    <p>{{ price2 }} 만원</p>
    <button @click="신고수[0] += 100">허위매물 신고</button> 
    <span>신고수 : {{ 신고수[0] }}</span>
  </div>

  <div>
    <h4>{{ products[1] }}</h4>
    <p>100 만원</p>
    <button @click="신고수[1]++">허위매물 신고</button> 
    <span>신고수 : {{ 신고수[1] }}</span>
  </div>

  <div>
    <h4>{{ products[2] }}</h4>
    <p>100 만원</p>
    <button @click="신고수[2]++">허위매물 신고</button> 
    <span>신고수 : {{ 신고수[2] }}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      price1 : 60,
      price2 : 80,
      신고수 : [0, 0, 0],
      menus : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
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
#app {
  font-family: 맑은고딕, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #222;
  margin: 0;
  padding: 0;
}

.menu {
  background: darkcyan;
  padding: 20px;
  margin-bottom: 50px;
  border-radius: 10px;
}
.menu a {
  color:#fff;
  padding:0 30px;
}
</style>
