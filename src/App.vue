<template>

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>




  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i">{{a}}</a>
  </div>

  <div v-for="(b,i) in products" :key="i">
    <img :src="원룸들[i].image" class="room-img">
    <h4 class="red" :style="스타일" @click="모달창열렸니 = true">{{원룸들[i].title}}</h4>
    <p>{{ 원룸들[i].price }} 원</p>
  </div>  

</template>

<script>


import 작명 from './assets/oneroom.js';
작명


export default {
  name: 'App',
  data(){
    return{
      원룸들 : 작명,
      모달창열렸니 : false,
      roomAddr : ['./assets/room0.jpg','./room1.jpg','./room2.jpg'],
      price : [60,70,80],
      신고수 : [0,0,0],
      스타일 : 'color : red',
      메뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸']
    }
  },

  methods: {
    increase(i){
      this.신고수[i]++;
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

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color: white;
  padding: 15px;
}

.room-img {
  width: 75%;
  margin-top: 40px;
}

body{
  margin: 0;
}

div{
  box-sizing: border-box;
}

.black-bg{
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}

.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

</style>
