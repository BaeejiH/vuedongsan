<template>

<!-- props(자식에게 데이터 보내는 법)
1. 데이터 보내고
2. 등록하고 
3. 가져다 쓰기
+ ex) <자식:데이터="데이터">
+ :  == v-bind랑 똑같음
-->
<!-- <div class="start" :class="{end : 모달창현재상태}"> <-- transition을 쓰지 않고 애니메이션을 적용하려할 때
transition으로 애니메이션을 주기위에서 style의 3가지 코드를 필요로함.
-->
<transition name="fade">
<ModalBanner 
  @closeModal="모달창현재상태 =false;"
  :마켓="마켓" 
  :사용자누름="사용자누름"  
  :모달창현재상태="모달창현재상태"
/>
</transition>

<!-- v-else-if (if문을 연달아 쓰고 싶을 때)-->
<div v-if="1 == 2">
  Hi
</div>

<div v-else>
  Hi 2
</div>

<!-- component문법
1. vue파일을 improt해오고 
2. components에 등록하고
3. 가져다 쓰기
+ component의 이름은 2단어 이상으로 작명해야함. ex) dis로 작명시 에러발생.
-->
 
 <!--동적UI 만드는법
    1. UI 현재 상태를 데이터로 저장
    2. 데이터에 따라 UI가 어떻게 보일지 작성 -->


<DisCountBanner :디스카운트="디스카운트"/>
<!-- 
  Lifecycle 
  웹 페이지에 표시되기까ㅓ지 일련의 step을 거침
  create 단계 -> mount단계-> 컴포넌트 생성 -> update 단계
  컴포넌트가 업데이트 , 랜더링이 되기전에 뭔가를 실행시킬 수 있음 ->Lifecycle hook 
-->


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
    <h2 @click="모달창현재상태 = true"> {{products[0]}}원룸</h2>
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
<button @click="priceSort">가격높은순정렬</button>
<button @click="sortBack">되돌리기</button>
<button @click="lowSort">가격낮은순정렬</button>
<button @click="koreaSort">가나다순정렬</button>
 <CardList 
  @openModal="모달창현재상태 = true; 사용자누름 = $event"
  :마켓="마켓[i]" v-for="(a,i) in 마켓" :key="a"
 />

  <!-- 자식 컴포넌트가 부모데이터를 변경할수 없음으로 메세지를 전송하는 방법으로 변경 $emit() -->

<!-- props를 보내는 여러가지 방법
  <CardList :데이터이름="[1,2,3]"/> Array
  <CardList :데이터이름="{age:20}"/> Object머
  <CardList :데이터이름="100"/> 숫자
  <CardList :데이터이름="안녕하세요"/> 문자
 -->

</template>

<script>

import data from './assets/data.js';
import market from './assets/market.js';
import DisCountBanner from './DisCountBanner.vue';
import ModalBanner from './ModalBanner.vue';
import CardList from './CardList.vue';

//함수를 쓰는 이유는 긴 코드를 짧은 코드로 요약하기 위해



export default {
  name: 'App',
  data(){
    return{
      //데이터 바인딩-> 실시간 자동 렌더링을 쓰기위해서
      //여기에 모든 데이터 저장해둬야 함
      //데이터는 odject 자료로 저장
      //데이터를 위에다 넣어줄 수 있음
      디스카운트 : 10,
      마켓오리지널 : [...market], // 같은 array를 별개로 저장하고 싶으면  ...으로 저장해야함
      사용자누름 : 0, // 사용자가 누른 번호가 모달창에 뜰 수 있도록
      마켓: market,
      상품목록: data,
      모달창현재상태: false,  
      신고수 : [0,0,0],
      메뉴들 : ['Home','shop','About'],
      원룸들 : ['금천구','시흥동','마포구'],
      pricel1 : 5000,
      pricel2 : 7000,
      price : [3000,4000,5000],
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
    },
    priceSort(){ // 숫자들을 정렬하고 싶을 때 .sort()  , 
      this.마켓.sort(function(a,b){
        return  b.price-a.price 
      })
    },
    sortBack(){
      // this.마켓 = this.마켓오리지널; // array 자료는 =로 연결하면 값을 공유해주는 역할만함.
      this.마켓 = [...this.마켓오리지널]; 
    },
    lowSort(){
      this.마켓.sort(function(a,b){
        return a.price -b.price
      })
    },
    koreaSort(){ //arrow function ---> 바깥에 있는 this를 잘 가져다 쓸 수 있음. this를 쓸 일이 있다면 다 arrow function으로 변경. 
      this.마켓.sort(function(a,b){
          return a.title.localeCompare(b.title,'ko');
        })
    },

  },

  mounted(){ // 메인페이지에 90의 값을 저장시켜놓고 props로 데이터를 넘겨준뒤 메인페이지에서 -1씩 감소하도록 설정
    setInterval(() => {
      this.디스카운트-=1;
      if(this.디스카운트 == 0){
        this. 디스카운트 =1;
      }
    }, 1000);
  },

  components: {
    DisCountBanner : DisCountBanner, // ket,value형식으로 위에서 import한것을 가져옴. 왼쪽 변수는 자유 작명가능. 왼쪽과 오른쪽이 같다면 DisCountBanner, <--이렇게도 가능
    ModalBanner : ModalBanner,
    CardList : CardList,
  }
}
</script>

<style>
.fade-enter-from{
  opacity: 0;
} 
.fade-enter-active{
  transition: all 1s;
}
.fade-enter-to{
  opacity: 1;
}


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
.DisCountBanner{
  background: #eee;
  padding: 10px;
  margin: 10px;
  border-radius: 5px;
}
</style>


