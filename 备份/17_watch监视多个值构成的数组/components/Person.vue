<script lang="ts" setup name="Person">
import { ref, watch, reactive } from "vue";

let person = reactive({
  name: "张三",
  age: 19,
  car: {
    c1: "奔驰",
    c2: "宝马",
  },
});
function changeName() {
  person.name += "~";
}
function changeAge() {
  person.age += 1;
}
function changeC1() {
  person.car.c1 = "大众";
}
function changeC2() {
  person.car.c2 = "红旗";
}
function changeCar() {
  person.car = { c1: "雅迪", c2: "小刀" };
  // Object.assign(person.car, { c1: "雅迪", c2: "小刀" });
}

// 监视的值是多个，使用数组包裹,
/* 
  1.监视对象的属性，使用getter函数
  2.监视对象的属性，同时本身又是一个对象，还是使用getter函数,加上deep:true
  3.这时候newValue,oldValue就是一整个数组的新值与旧值
*/
watch(
  [() => person.name, () => person.car],
  (newValue, oldValue) => {
    console.log("name发生了变化", newValue, oldValue);
  },
  { deep: true }
);
</script>

<template>
  <div class="person">
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <h2>汽车：{{ person.car.c1 }}-{{ person.car.c2 }}</h2>
    <button @click="changeAge">修改年龄</button>
    <button @click="changeName">修改名字</button>
    <button @click="changeC1">修改第一台车</button>
    <button @click="changeC2">修改第二台车</button>
    <button @click="changeCar">修改全部车</button>
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
