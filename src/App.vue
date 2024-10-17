<template>
 
<div class="menu">
  <a v-for="a in 메뉴들" :key="a">{{a}}</a> 
  <!-- 
  1. 자료안의 데이터 갯수만큼 반복됨
  2. 작명한 변수는 데이터안의 자료가됨
  3. v- for (반복문) 사용할때 key 꼭 써야함.
  -->
</div>


  
  <div>
    <h2 :style="스타일"> {{products[0]}}원룸</h2>
    <p>500만원</p>
  </div>

  <div>
    <h2 :style="스타이일">{{products[1]}} 원룸</h2>
    <p>700만원</p>
  </div>

  <div>
    <h2 :style="스타이이일">{{products[2]}} 원룸</h2>
    <p>1000만원</p>
  </div>

  <div>
    <a v-for="a1 in 원룸들" :key="a1" style="display:block;">{{a1}}</a>
  </div>
</template>

<script>



export default {
  name: 'App',
  data(){
    return{
      //데이터 바인딩-> 실시간 자동 렌더링을 쓰기위해서
      //여기에 모든 데이터 저장해둬야 함
      //데이터는 odject 자료로 저장
      //데이터를 위에다 넣어줄 수 있음
      메뉴들 : ['Home','shop','About'],
      원룸들 : ['금천구','시흥동','마포구'],
      pricel1 : 5000,
      pricel2 : 7000,
      rogo : '원룸',
      스타일 : 'color : red',
      스타이일 : 'color : blue',
      스타이이일 : 'color : purple',
      products : ['역상동 원룸','천호동원룸','마포구원룸']
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background-color: rgb(24, 30, 137);
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color:white;
  padding: 10px;
}
</style>


