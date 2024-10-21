<template>
  <div class="black-bg" v-if="모달창현재상태 == true">
  <div class="white-bg">
    <img src="./assets/home1.jpeg" class="W-img">
    <h4>{{마켓[사용자누름].title}}</h4>
    <p>{{마켓[사용자누름].content}}</p>
    <p>{{마켓[사용자누름].price}}억</p>
  <!-- <button @click="모달창현재상태 = false">닫기</button> -->
  </div>
</div>
</template>

<script>
export default {
    name : 'ModalBanner',
    props : {
      마켓 : Array,
      사용자누름:Number,
      모달창현재상태:Boolean,
    }
}
</script>

<style>

</style>