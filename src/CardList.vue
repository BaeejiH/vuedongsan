<template>
  <!-- custom Event
  1. 자식이 부모데이터를 수정해야할 때
  2. message를 보내는형식으로
  3. $emit()
  4. $event -->

  <div>
    <img :src="마켓.image" class="W-img">
    <h2 @click="$emit('openModal',마켓.id)">{{마켓.title}}</h2>
    <p>{{마켓.price}}억</p>
    <p>{{마켓.content}} </p>
  </div>
</template>

<script>    

export default {    
    name : 'CardList',
    props : {
      마켓:Object,
    }, //  원룸 데이터를 CardList.vue로 props 전송
    
}
</script>

<style>

</style>