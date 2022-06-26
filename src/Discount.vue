<template>
  <div class="discount">
    <h4>지금 결제하면 <span>{{ amount }}</span>% 할인</h4>
  </div>
</template>

<script>
export default {
  name: 'App',
  props : {
    amount : Number,
  }
}
</script>

<style>

</style>