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

/*
仅仅监视对象中的某一个属性,如果这个属性是基本类型，第一个参数需要写成getter函数形式
*/
watch(
  () => person.name,
  (newValue, oldValue) => {
    console.log("name发生了变化", newValue, oldValue);
  }
);

/*
如果这个属性又是一个对象，可以直接写，也可以用getter函数的形式，最好是使用函数形式
1. person.car形式，可以监视到对象内部属性c1，c2变化，但是直接覆盖person.car={}不能监视到，
这就是reactive的局限性，可以使用Object.assign(person.car, { c1: "雅迪", c2: "小刀" });这种形式
但是很麻烦
 */
/* watch(person.car, (newValue, oldValue) => {
  console.log("car发生了变化", newValue, oldValue);
}); */

/* 
  2. 监视的属性还是一个对象，使用getter函数形式返回
  同时加上deep:true，就可以监视到内部属性的变化以及整个对象的变化
*/
watch(
  () => person.car,
  (newValue, oldValue) => {
    console.log("car发生了变化", newValue, oldValue);
  },
  {
    deep: true,
  }
);

// 总结：结论就是监视对象内部的属性的时候，直接使用getter函数的形式，如果这个属性又是一个对象，
// 就加上{deep:true}参数
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
