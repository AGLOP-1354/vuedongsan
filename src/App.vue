<template>

  <!-- 메뉴 -->
  <Menu :menus="menus"/>

  <!-- 모달창 -->
  <Modal 
  @closeModal="modal_state = false"
  :modal_number="modal_number" 
  :modal_state="modal_state" 
  :products="products" 
  />

  <!-- 할인 모달 -->
  <Discount />

  <!-- 상품 카드 -->
  <ItemList
  @openModal="modal_state = true, modal_number = i"
  :modal_number="modal_number" 
  :modal_state="modal_state" 
  :products="products[i]" 
  v-for="(a,i) in products" :key="a"
  />



</template>

<script>
import Item_info from './assets/post.js'
import Discount from './components/Discount.vue'
import ItemList from './components/ItemList.vue'
import Modal from './components/Modal.vue'
import Menu from './components/Menu.vue'

export default {
  name: 'App',
  data(){
        return {
            modal_number : 0,
            modal_state : false,
            menus : ["Home", 'Products', "About"],
            products : Item_info
            }
    },
  components: {
    Discount : Discount,
    ItemList : ItemList,
    Modal : Modal,
    Menu : Menu
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
</style>
