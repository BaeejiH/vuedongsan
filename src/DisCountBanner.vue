<template>
  <div class="DisCountBanner">
   <h4>지금 결제하면 {{디스카운트}}% 할인을해준다고?</h4>
  </div>
</template>

<script>
//component 생성방법
//1. vue파일 생성  2. 축약할 HTML 넣기 3. name넣기는 선택
export default {
    name: 'DisCountBanner',
    props:{
      디스카운트:Object,
    }
}
</script>

<style>

</style>