<template>
  <div class="black-bg" v-if="모달창현재상태 == true">
  <div class="white-bg">
    <img :src="마켓[사용자누름].image" class="W-img">
    <h4>{{마켓[사용자누름].title}}</h4>
    <p>{{마켓[사용자누름].content}}</p>
    <!-- 
    -<input @input="month = $event.target.value"> 
    -아래 v-model을 복잡하게 
    -input에 입력한 데이터를 아래에 데이터에 넣어줌
    -<textarea v-model="month"></textarea>
    -사용자가 <input>에 입력한 것은 전부 문자자료형
    -무조건 숫자로 나태내고 싶다면 .number을 붙여줘야함
    -->
    <input v-model.number="month">  
    <p>{{month}}개월 선택함:{{마켓[사용자누름].price*month}}억</p>
  <button @click="$emit('closeModal')">닫기</button>
  <!-- 닫기버튼이 안열리는오류 문제(Type Error) = closeModal에 ''를 넣지 않고 부모에게 데이터를 보냄.  
  -->
  </div>
</div>
</template>

<script>
export default {
    name : 'ModalBanner',
    data(){
      return{
        month : 1,// 초기값의 type이 매우 중요함.
      }
    },
    // watch : {감시하 데이터(){}}
    // 문자를 입력했을때 경고창 + 개월수 다시1로 되돌리기
    // isNaN = 자바스크립트에서 어떠한 값이 숫자가 아닌지 여부를 판별하는 함수
    watch : {
      month(a){
        if (typeof a === 'string' && isNaN(a)){
          alert('문자는 입력할 수 없습니다')
          this.month = 1;
        }
      }
    },
    props : {
      마켓 : Array,
      사용자누름:Number,
      모달창현재상태:Boolean,
    },
    
     beforeUpdate() {
    if(this.month == 5){
      alert('5개월은 너무 애매함')
    }
  },
}
</script>

<style>

</style>