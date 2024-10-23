<template>
  <div>
    <img src="./assets/W4.webp" class="W-img">
    <h2>{{원룸들}}</h2>
    <p>{{price}}억</p>
  </div>
</template>

<script>    
export default {    
    name : 'CardList',
    props : {
      원룸들 : Array, //  원룸 데이터를 CardList.vue로 props 전송
      price : Array,
    }
}
</script>

<style>

</style>