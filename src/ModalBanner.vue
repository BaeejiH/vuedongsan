<template>
  <div class="black-bg" v-if="모달창현재상태 == true">
  <div class="white-bg">
    <img :src="마켓[사용자누름].image" class="W-img">
    <h4>{{마켓[사용자누름].title}}</h4>
    <p>{{마켓[사용자누름].content}}</p>
    <p>{{마켓[사용자누름].price}}억</p>
  <button @click="$emit('closeModal')">닫기</button>
  <!-- 닫기버튼이 안열리는오류 문제(Type Error) = closeModal에 ''를 넣지 않고 부모에게 데이터를 보냄.  
  -->
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