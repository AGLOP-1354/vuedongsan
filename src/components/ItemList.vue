<template>
    <div>
        <img :src="products.image" class="room-img">
        <h4 @click="$emit('openModal')" class="modal_open">{{ products.title }}</h4>
        <p>{{ products.price }} 원</p>
    </div>
</template>

<script>

export default {
    name : 'ItemList',
    props : {
        modal_number : Object,
        modal_state : Object,
        products : Array
    }
}
</script>

<style>
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.room-img{
  width: 100%;
  margin-top: 5px;
  padding: 15px;
}
.modal_open{
  cursor: pointer;
}
</style>