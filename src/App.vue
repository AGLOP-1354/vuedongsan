<template>

  <div class="black-bg" v-if="modal_state == true">
    <div class="white-bg">
      <img :src="products[modal_number].image" >
      <h4>{{ products[modal_number].title }}</h4>
      <p>{{ products[modal_number].content }}</p>
      <p>{{ products[modal_number].price }} 원</p>
      <button @click="modal_state = false">닫기</button>
    </div>
  </div>


  <div class="menu">
    <a v-for="menu_item in menus" :key="menu_item" >{{ menu_item }}</a>
  </div>

  <div v-for="(a,i) in products" :key="i">
    <img :src="products[i].image" class="room-img">
    <h4 @click="modal_state = true, modal_number = i" class="modal_open">{{ products[i].title }}</h4>
    <p>{{ products[i].price }} 원</p>
  </div>
  <!-- <div>
    <img :src="products[1].image" class="room-img">
    <h4 @click="modal_state = true">{{ products[1].title }}</h4>
    <p>80 만원</p>
  </div>
  <div>
    <img :src="products[2].image" class="room-img">
    <h4 @click="modal_state = true">{{ products[2].title }}</h4>
    <p>45 만원</p>
  </div> -->


</template>

<script>
import Item_info from './assets/post'

export default {
  name: 'App',
  data(){
    return {
      modal_number : 0,
      modal_state : false,
      신고수 : [0, 0, 0],
      menus : ["Home", 'Products', "About"],
      products : Item_info
    }
  },
  methods : {
    increase(){
      this.신고수++
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
body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.menu {
  background : darkslateblue;
  padding : 15px;
  border-radius : 5px;
}
.menu a {
  color : white;
  padding : 10px;
}
.room-img{
  width: 100%;
  margin-top: 5px;
  padding: 15px;
}
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
.modal_open{
  cursor: pointer;
}
</style>
