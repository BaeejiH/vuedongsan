<template>
 
 <!--동적UI 만드는법
    1. UI 현재 상태를 데이터로 저장
    2. 데이터에 따라 UI가 어떻게 보일지 작성 -->
<div class="black-bg" v-if="모달창현재상태 == ture">
  <div class="white-bg">
    <h4>상세페이지임</h4>
    <p>상세페이지 내용</p>
  <button @click="모달창현재상태 = false">닫기</button>
  </div>
</div>



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
<hr>
  <div>
    <a v-for="a1 in 원룸들" :key="a1" style="display:block;">{{a1}}</a>
  </div>
<!--
  div에 그냥 v-for 넣어서 반복문 쓰면 아래와 같이도 구현가능 
  a는 products안에 있는 데이터가 되고, i는 반복되는 횟수를 나타냄
 -->
  <div v-for="(a,i) in 3" :key="i">
    <h2>{{products[i]}}</h2>
    <p>50만원</p>
  </div>
<hr>
<!--이벤트 핸들러 -->


  <div>
    <h2 @click="모달창현재상태 = ture"> {{products[0]}}원룸</h2>
    <img src="./assets/W2.jpg" class="W-img">
    <p>5만원</p>
    <button @mouseover="increase">허위매물신고</button> <span>신고수 : {{신고수[0]}}</span>
  </div>

  <div>
    <h2>{{products[1]}} 원룸</h2>
    <img src="./assets/W3.jpg" class="W-img">
    <p>7만원</p>
    <button @click="decrease">허위매물신고</button> <span>신고수 : {{신고수[1]}}</span>
  </div>

  <div>
    <h2>{{상품목록[0].title}}</h2>
     <img src="./assets/W4.webp" class="W-img">
    <p>{{상품목록[0].price}}억</p>
    <button @click="decrease1">허위매물신고</button> <span>신고수 : {{신고수[2]}}</span>
  </div>
  <hr>

   <div>
    <h2>{{마켓[0].title}}</h2>
     <img src="./assets/home1.jpeg" class="W-img">
    <p>{{마켓[0].price}}억</p>
    <p>{{마켓[0].content}}</p>
    <button @click="decrease1">허위매물신고</button> <span>신고수 : {{신고수[2]}}</span>
  </div>

   <div>
    <h2>{{마켓[1].title}}</h2>
     <img src="./assets/home1.jpeg" class="W-img">
    <p>{{마켓[1].price}}억</p>
    <p>{{마켓[1].content}}</p>
    <button @click="decrease1">허위매물신고</button> <span>신고수 : {{신고수[2]}}</span>
  </div>

   <div>
    <h2>{{마켓[2].title}}</h2>
     <img src="./assets/home1.jpeg" class="W-img">
    <p>{{마켓[2].price}}억</p>
    <p>{{마켓[2].content}}</p>
    <button @click="decrease1">허위매물신고</button> <span>신고수 : {{신고수[2]}}</span>
  </div>

</template>

<script>

import data from './assets/data.js';
import market from './assets/market.js';

//함수를 쓰는 이유는 긴 코드를 짧은 코드로 요약하기 위해

export default {
  name: 'App',
  data(){
    return{
      //데이터 바인딩-> 실시간 자동 렌더링을 쓰기위해서
      //여기에 모든 데이터 저장해둬야 함
      //데이터는 odject 자료로 저장
      //데이터를 위에다 넣어줄 수 있음
      마켓: market,
      상품목록: data,
      모달창현재상태: false,  
      신고수 : [0,0,0],
      메뉴들 : ['Home','shop','About'],
      원룸들 : ['금천구','시흥동','마포구'],
      pricel1 : 5000,
      pricel2 : 7000,
      rogo : '원룸',
      스타일 : 'color : red',
      스타이일 : 'color : blue',
      스타이이일 : 'color : purple',
      products : ['역삼동','천호동','마포구']
    }
  },
  methods: {
    //data에 있는 신고수를 가져다 쓰고 싶으면 앞에 this.을 붙여줘야 가져와서 쓸 수 있음.
    increase(){
      this.신고수[0] ++;
    },
    decrease(){
      this.신고수[1]--;
    },
     decrease1(){
      this.신고수[2]--;
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
.W-img{
  width: 30%;
  margin-top: 40px;
}
body{
  margin: 0
}
div{
  box-sizing: border-box;
}
.black-bg{
  width: 100%; height: 100%;
  background: rgb(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>


