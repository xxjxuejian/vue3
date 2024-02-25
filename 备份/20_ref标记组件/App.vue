<script lang="ts" setup name="App">
import Person from "./components/Person.vue";
import { ref } from "vue";

let child = ref();

/* 
  使用ref标记子组件，可以获取到子组件的实例对象，还可以拿到子组件内部的数据或者方法
  前提是子组件已经暴露了这些属性
*/

function getChild() {
  console.log(child.value);
  // 子组件的实例对象以及暴露的属性和方法
  // Proxy(Object) {name: 'xxj', __v_skip: true, showH2: ƒ}
}
</script>

<template>
  <div class="app">
    <h1>App父组件</h1>
    <button @click="getChild">获取子组件</button>
    <Person ref="child"></Person>
  </div>
</template>

<style scoped>
.app {
  background-color: #ddd;
  box-shadow: 0 0 10px;
  border-radius: 10px;
  padding: 20px;
}
</style>
