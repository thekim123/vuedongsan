<template>
  <Transition name="fade">
    <ModalCard @closeModal="모달창열렸니=false" 
    :모달창열렸니="모달창열렸니" 
    :원룸들="원룸들" :누른거="누른거"/>
  </Transition>

  <div class="menu">
    <a v-for="(a, i) in 메뉴들" :key="i">{{a}}</a>
  </div>

  <button @click="titleSort">이름순</button>
  <button @click="priceSortAsc">가격순</button>
  <button @click="priceSortDesc">가격역순</button>
  <button @click="belowFifty">50만원이하</button>
  <button @click="sortBack">되돌리기</button>

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
      원룸들오리지널 : [...작명],
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
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];      
    },
    priceSortAsc(){
      this.원룸들.sort(function(a, b){
          return a.price-b.price;
      });
    },
    priceSortDesc(){
      this.원룸들.sort(function(a, b){
          return b.price-a.price;
      })
    },
    titleSort(){
      this.원룸들.sort(function(a, b){        
        if(a.title<b.title){
          return -1;
        } 
        
        if(a.title>b.title){
          return 1;
        }
        
        else{
          return 0;
        }
      })
    },
    belowFifty(){
      const newArr= [];
      this.원룸들.forEach((oneRoom)=>{
        if(oneRoom.price<=500000) newArr.push(oneRoom);
      })
      this.원룸들= newArr;
    },
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

/* .start{
  opacity: 0;
  transition: all 1s;
}

.end{
  opacity: 1;
  transition: all 1s;
} */

.fade-enter-from {
  /* opacity: 0; */
  transform: translateY(-1000px);
}

.fade-enter-active{
  transition: all 1s;
}

.fade-enter-to{
  /* opacity: 1; */
  transform: translateY(0px);
}

.fade-leave-from {
  /* opacity: 1; */
  transform: translateY(0px);
}

.fade-leave-active{
  transition: all 1s;
}

.fade-leave-to{
  /* opacity: 0; */
  transform: translateY(-1000px);
}

</style>
