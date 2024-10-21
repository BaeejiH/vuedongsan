<template>
  <div v-for="(a,i) in 3" :key="i">
    <!-- <h2 @click="모달창현재상태 = true; 사용자누름 = i;">{{마켓[i].title}}</h2> -->
    <h2>{{원룸들[i]}}원룸</h2>
     <img src="./assets/home1.jpeg" class="W-img">
     <p>{{price[i]}}억</p>
    <!-- <button @click="decrease1">허위매물신고</button> <span>신고수 : {{신고수[2]}}</span> -->
  </div>
</template>

<script>    
export default {    
    name : 'CardList',
    props : {
        원룸들 : Array,
        price : Array,
    }
}
</script>

<style>

</style>