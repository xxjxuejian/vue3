<script lang="ts" setup name="Person">
import { ref, watch } from "vue";

let sum = ref(0);

function changeSum() {
  sum.value += 1;
}

// 1. 这里监视的时候，sum不需要使用.value
// 2. 解除监视，watch()的返回值是一个函数，这个函数可以用来停止监视
const stopWatchFn = watch(sum, (newValue, oldValue) => {
  console.log("sum变化了", newValue, oldValue);

  if (newValue > 10) {
    stopWatchFn();
  }
});
</script>

<template>
  <div class="person">
    <h1>情况一：监视【ref】定义的【基本类型】的数据</h1>
    <h2>sum:{{ sum }}</h2>
    <button @click="changeSum">修改sum</button>
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
