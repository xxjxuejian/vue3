<script lang="ts" setup name="Person">
import { ref, watch, reactive, watchEffect } from "vue";

let temp = ref(10);
let height = ref(0);

function changeTemp() {
  temp.value += 10;
}
function changeHeight() {
  height.value += 10;
}

// 如果监视的数据过多的时候，数组中就需要写很多值，比较麻烦
/* watch([temp, height], (newValue) => {
  let [t, h] = newValue;
  if (t >= 60 || h >= 80) {
    console.log("发送请求了");
  }
}); */

// 使用watchEffect实现监视，会自动识别出内部需要监视的数据
// 它会立即执行这个监视函数，当数据发生变化时会再次执行
watchEffect(() => {
  if (temp.value >= 60 || height.value >= 80) {
    console.log("发送请求了");
  }
});

/* 
watch 要明确的指出需要监视的数据
watchEffect 不用明确的指出监视的数据，函数中用到哪些属性就监视哪些属性
*/
</script>

<template>
  <div class="person">
    <h2>需求：水温达到60度，或者水位达到80cm,给服务器发生请求</h2>
    <h2>当前水温：{{ temp }}</h2>
    <h2>当前水位：{{ height }}</h2>
    <button @click="changeTemp">水温＋10</button>
    <button @click="changeHeight">水位＋10</button>
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
