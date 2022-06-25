<template>
  <div class="black-bg" v-if="modalOpen == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" />
      <h4>{{ 원룸들[누른거].title }}</h4>
      <p>{{ 원룸들[누른거].content }}</p>

      <input v-model.number="month">
      <!-- <input @input="month = $event.target.value"> -->
      <input type="range" min="1" max="12"><br>      
      <textarea v-model="month"></textarea><br>
      <select v-model="month"><br>
        <option>1</option>
        <option>2</option>
        <option>10</option>
      </select>

      <p>{{ month }}개월 선택함 : <del>{{ 원룸들[누른거].price}}</del> {{ 원룸들[누른거].price + month}} 원</p>

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
  watch : {
    //month 라는 데이타가 변할때마다 여기있는 코드 실행됨
    //Vue 전용 form validation 라이브러리 watcher안써두 됨
    month(a){ 
      if ( a >= 13 ){
        alert('13이상 입력하지 마셈');
        this.val( this.val().replace(/[^0-9]/gi,"") );
      }      
    },
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