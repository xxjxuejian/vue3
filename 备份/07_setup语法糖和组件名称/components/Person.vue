<!-- 
  这个可以是单独配置组件名称的script，但是好像有点没必要
  可以通过一个插件，配置组件的名称
  安装插件npm i vite-plugin-vue-setup-extend -D
  在vite.config.ts中引入，import VueSetupExtend from "vite-plugin-vue-setup-extend";
  配置plugins:   plugins: [vue(), VueSetupExtend()],
  在组件的script中添加name='组件名称'
<script lang="ts">
export default {
  name: "Person",
};
</script> 
-->

<!-- setup语法糖 ：相当于内部的代码写在了setup(){}之中，也做了返回，而且连export default也省略了-->
<script lang="ts" setup name="person123">
let name = "张三";
let age = 18;
let tel = 13739320023;

function changeName() {
  name = "zhang-san";
}
function changeAge() {
  age += 1;
}
function showTel() {
  alert(tel);
}
</script>

<template>
  <div class="person">
    <h2>姓名{{ name }}</h2>
    <h2>年龄{{ age }}</h2>
    <button @click="changeName">修改姓名</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="showTel">查看联系方式</button>
  </div>
</template>

<style scoped>
.person {
  background-color: skyblue;
  box-shadow: 0 0 10px;
  border-radius: 10px;
  padding: 20px;
}
button {
  margin: 0 5px;
}
</style>
