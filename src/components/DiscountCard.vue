<template>
  <div class="discount">
    <h4>지금 결제하면 {{discountRate}} 할인</h4>
  </div>
</template>

<script>
export default {
    name:'DiscountCard',
    props:{
        discountRate: Number,
    },

    mounted() {
        setInterval(()=>{
            this.$emit('reduceDiscountRate');
        }, 1000);
    },
}


</script>

<style>

</style>