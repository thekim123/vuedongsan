<template>

  <ModalCard @closeModal="모달창열렸니=false" :모달창열렸니="모달창열렸니" :원룸들="원룸들" :누른거="누른거"></ModalCard>

  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i">{{a}}</a>
  </div>

  <ProductCard @openModal="모달창열렸니=true; 누른거=$event" v-for="(oneRoom, i) in 원룸들" :key="oneRoom" :oneRoom="원룸들[i]" :모달창열렸니="모달창열렸니" :누른거="누른거"/>
</template>

<script>


import 작명 from './assets/oneroom.js';
import ModalCard from './components/ModalCard.vue';
import ProductCard from './components/ProductCard.vue';

export default {
  name: 'App',
  data(){
    return{
      원룸들 : 작명,
      모달창열렸니 : false,
      스타일 : 'color : red',
      메뉴들 : ['Home', 'Shop', 'About'],
      누른거 : 0,
    }
  },

  methods: {
    increase(i){
      this.신고수[i]++;
    }
  },

  components: {
    ModalCard: ModalCard,
    ProductCard: ProductCard,
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
  width: 50%;
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
