<template>
  <div class="black-bg" v-if="modalOpen == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>

      <!-- <input type="text" v-model.number="month"> -->
      <input type="text" @input="month = $event.target.value" :value="month">
      <!-- <input type="range" min="1" max="12"><br>
      <textarea v-model="month"></textarea><br>
      <select v-model="month"><br>
        <option>1</option>
        <option>2</option>
        <option>10</option>
      </select> -->

      <p>{{ month }}개월 선택함 : <del>{{ 원룸들[누른거].price}}</del> {{ 원룸들[누른거].price * month}} 원</p>

      <button @click="sendclose">닫기</button>
      <!-- <button @click="modalOpen = false">닫기</button> 부모요소라 사용할수 없음 
      <button @click="$emit('closeModal')">닫기</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      month : 1, //문자 초기값 : 'dsff', 숫자 초기값 : 1
    }
  },
  beforeUpdate(){
    if ( this.month == 2 ){
      alert('2개월은 안팝뉘다.')
    }
  },
  watch : {
    //month 라는 데이타가 변할때마다 여기있는 코드 실행됨
    //Vue 전용 form validation 라이브러리 watcher안써두 됨
    month(a){ 
      if ( a >= 13 ){
        alert('13이상 입력하지 마셈');
        this.month = 1;
      }

      //month 라는 데이타를 isNaN() 안에 집어넣어보고 true 가 나오면 alert 띄우셈      
      // if ( isNaN(parseFloat(a)) == true ){
      //   alert('문자 입력하지마라');
      //   this.month = 1;
      // }
      
      //https://pygmalion0220.tistory.com/entry/Vue-input%EC%97%90-%EC%88%AB%EC%9E%90%EB%A7%8C-%EC%9E%85%EB%A0%A5-%EA%B0%80%EB%8A%A5%ED%95%98%EA%B2%8C-%ED%95%98%EA%B8%B0
      const reg = /[ㄱ-ㅎ|ㅏ-ㅣ|가-힣|a-z]/;
      if(reg.exec(a)!==null) {
        this.month = a.replace(/[^0-9]/g,'');
        alert('문자 입력하지마라');
      }
      if ( isNaN(parseFloat(a)) ){
        this.month = '';
      }
    }
  },
  props : {
    원룸들 : Array, 
    누른거 : Number,
    modalOpen : Boolean,
  },
  methods : {
    sendclose() {
      this.$emit('closeModal')
    },
  },
}
</script>

<style>

</style>