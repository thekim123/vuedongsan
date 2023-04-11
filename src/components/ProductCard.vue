<template>
    <div>
        <img :src="oneRoom.image" class="room-img">
        <h4 class="red" :style="스타일" @click="send();">{{oneRoom.title}}</h4>
        <p>{{ oneRoom.price }} 원</p>
    </div>    
</template>

<script>
export default {
    name: 'ProductCard',
    props:{
        oneRoom: {
            type: Object,
        },
    },
    methods: {
        send(){
            this.$emit('openModal', this.oneRoom.id);
        }
    }
}
</script>

<style>

</style>