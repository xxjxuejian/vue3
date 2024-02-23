<script lang="ts" setup name="Person">
import { ref, reactive } from "vue";

// reactive处理对象类型
let car = reactive({
  brand: "BMW",
  price: 100,
});

// 方法
function changePrice() {
  car.price += 10;
}
function changeCar() {
  // 直接修改整个汽车对象,替换了之前的对象,car就失去了之前的响应式
  // car = { brand: "byd", price: 10 };
  // car = reactive({ brand: "byd", price: 10 });

  // 可行的方法
  Object.assign(car, { brand: "byd", price: 10 });

  // 或者是使用ref定义这个对象，通过.value的方式不失去响应式
  /*  
  car = ref({ brand: "byd", price: 10 });
  car.value = {brand: "雅迪", price: 1 }
  */

  /* 
  使用原则：
  1. 需要一个基本类型的响应式数据，必须使用ref
  2. 需要一个响应式对象，层级不深，ref,和reactive都可以
  3. 需要一个响应式对象，层级较深，或者是表单类型的数据，推荐使用reactive
  */
}
</script>

<template>
  <div class="person">
    <h2>一辆{{ car.brand }}车，价值{{ car.price }}万</h2>
    <button @click="changePrice">修改汽车的价格</button>
    <button @click="changeCar">修改汽车</button>
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
