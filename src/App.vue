<template>

  <!-- 메뉴 -->
  <Menu :menus="menus"/>

  <!-- 모달창 -->
  <transition name="fade">
    <Modal 
    @closeModal="modal_state = false"
    :modal_number="modal_number" 
    :modal_state="modal_state" 
    :products="products" 
    />
  </transition>

  <!-- 할인 모달 -->
  <Discount v-if="showDiscount == true" :sale="sale"/>


  <button @click="Back">기본</button>
  <button @click="priceLow">낮은 가격 순</button>
  <button @click="priceHigh">높은 가격 순</button>
  <button @click="ABC">이름 순</button>
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
            showDiscount : true,
            sale : 30,
            originProducts : [...Item_info],
            modal_number : 0,
            modal_state : false,
            menus : ["Home", 'Products', "About"],
            products : Item_info
            }
    },
    methods: {
      priceLow(){
        this.products.sort(function(a,b){
          return a.price - b.price
        })
      },
      Back(){
        this.products = [...this.originProducts];
      },
      priceHigh(){
        this.products.sort(function(a,b){
          return b.price - a.price
        })
      },
      ABC(){
        this.products.sort(function(a,b){
          return a.title.localeCompare(b.title)
        })
      }
    },
    mounted(){
      setInterval(()=>{
        this.sale -= 1
        if(this.sale == 0){
          this.showDiscount = false
        }
      }, 1000)
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
.fade-enter-from {
  opacity: 0;
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  opacity: 1;
}
.fade-leave-from {
  opacity: 1;
}
.fade-leave-active {
  transition: all 1s;
}
.fade-leave-to {
  opacity: 0;
}
</style>
