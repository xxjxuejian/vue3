<!-- setup语法糖 ：相当于内部的代码写在了setup(){}之中，也做了返回，而且连export default也省略了-->
<script lang="ts" setup name="Person">
import { ref } from "vue";
// ref包裹以后，数据变成响应式的，在js中是使用需要加上.value，在模板中可以不加

let name = ref("张三");
let age = ref(18);
let tel = 13739320023;

console.log(name);
console.log(age);
console.log(tel);

function changeName() {
  name.value = "zhang-san";
}
function changeAge() {
  age.value += 1;
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
