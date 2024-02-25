<script lang="ts" setup name="Person">
import { ref } from "vue";

let name = "xxj";

function showH2() {
  console.log("子组件的方法");
}

// 向父组件暴露的东西
defineExpose({
  name,
  showH2,
});
</script>

<template>
  <div class="person">
    <h1>中国</h1>
    <h2>北京</h2>
    <h3>尚硅谷</h3>
    <button>输出h2元素</button>
  </div>
</template>

<style scoped>
.person {
  background-color: skyblue;
  box-shadow: 0 0 10px;
  border-radius: 10px;
  padding: 20px;
}
.red {
  color: red;
}
button {
  margin: 0 5px;
}
</style>
