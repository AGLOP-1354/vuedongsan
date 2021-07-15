<template>
    <div class="black-bg" v-if="modal_state == true">
        <div class="white-bg">
        <img :src="products[modal_number].image" >
        <h4>{{ products[modal_number].title }}</h4>
        <p>{{ products[modal_number].content }}</p>
        <p>{{ products[modal_number].price }} 원</p>
        <button @click="$emit('closeModal')">닫기</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Modal',
    props : {
        modal_number : Object,
        modal_state : Object,
        products : Object
    }
}
</script>

<style>
.black-bg {
  width: 100%; 
  height:100%;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 80%;
  background: white;
  border-radius: 8px;
  padding: 20px;
} 
.white-bg img{
  max-width: 80%;
}
</style>