<template>
    <div class="black-bg" v-if="modal_state == true">
        <div class="white-bg">
        <img :src="products[modal_number].image" >
        <h4>{{ products[modal_number].title }}</h4>
        <p>{{ products[modal_number].content }}</p>
        <input  v-model="month">
        <p> {{month}}개월 선택함 : {{ products[modal_number].price * month}} 원</p>
        <button @click="$emit('closeModal')">닫기</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Modal',
    data(){
        return{
            month : 1
        }
    },
    props : {
        modal_number : Object,
        modal_state : Object,
        products : Object
    },
    watch : {
        month(a){
            if(a >= 13){
                alert('12이하의 숫자를 선택해주세요')
                this.month=1
            }
            if(isNaN(a) == true){
                alert('숫자를 입력해주세요')
                this.month = 1
            }
        }
    }
}
</script>

<style>
.black-bg {
  width: 100%; 
  height:100%;
  display: flex;
  top: 0;
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