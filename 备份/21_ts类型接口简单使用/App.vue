<script lang="ts" setup name="App">
import Person from "./components/Person.vue";
import { reactive } from "vue";
let persons = reactive([
  { id: 1, name: "张三", age: 18, address: "广州" },
  { id: 2, name: "李四", age: 20, address: "北京" },
]);
</script>

<template>
  <div class="app">
    <h1>App父组件</h1>
    <Person :persons="persons"></Person>
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
