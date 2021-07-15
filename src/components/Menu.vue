<template>
    <div class="menu">
        <a v-for="i in menus" :key="i" >{{ i }}</a>
    </div>
</template>

<script>
export default {
    name : 'Menu',
    props : {
        menus : Object
    }
}
</script>

<style>
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
</style>