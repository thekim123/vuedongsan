<template>
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <img :src="원룸들[누른거].image" class="room-img">
      <h4>{{원룸들[누른거].title}}</h4>
      <p>{{원룸들[누른거].content}}</p>
      <input v-model="month" @blur="checkInput">
      <p> {{ month }} 개월 선택함 : {{ Number(원룸들[누른거].price) * Number(month) }} 원</p>
      <button @click="send();">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
    name:'ModalCard',
    data(){
      return {
        month: '1',
      }
    },
    props:{
        모달창열렸니 : Boolean,
        원룸들: Array,
        누른거: Number,
    },
    methods: {
      send(){
        this.$emit('closeModal');
      },
      checkInput() {
        console.log(this.month);
        if (/^[0-9]+$/.test(this.month)) {
          console.log('입력값이 숫자로만 이루어져 있습니다.');
        } else {
          const invalidChars = this.month.replace(/[0-9]/g, '');
          alert(`숫자 외의 문자 ${invalidChars}가 포함되어 있습니다. 숫자로만 입력해주세요!`);
          this.month = '1';
        }
      }
    },
    watch: {
      month(a){
       if(isNaN(a)){
        alert('문자입력하지마라.... 뒤진다....');
        this.month='1';
       }
      }
    },
}
</script>

<style>

</style>