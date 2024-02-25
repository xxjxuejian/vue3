<script lang="ts" setup name="Person">
import { ref } from "vue";

// 创建一个title,用于存储ref标记的内容
// 用ref标记元素，不会导致重复，如果不同页面中还是像以前一样使用id标记元素，还是存在重复的情况的
let title = ref();

function showH2() {
  console.log(title.value);
}
</script>

<template>
  <div class="person">
    <h1>中国</h1>
    <h2 ref="title" class="red">北京</h2>
    <h3>尚硅谷</h3>
    <button @click="showH2">输出h2元素</button>
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
