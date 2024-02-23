<script lang="ts" setup name="Person">
import { ref, reactive } from "vue";

// 数据
// ref处理基本类型和对象类型，但是对于对象类型，底层调用的还是reactive
let car = ref({
  brand: "奔驰",
  price: 100,
});

// reactive处理对象类型
let obj = reactive({
  a: 100,
});

console.log(car);
console.log(obj);

// 方法
function changePrice() {
  car.value.price += 10;
}
</script>

<template>
  <div class="person">
    <h2>一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
    <button @click="changePrice">修改汽车的价格</button>
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
