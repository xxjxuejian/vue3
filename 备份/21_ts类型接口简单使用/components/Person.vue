<script lang="ts" setup name="Person">
import { type PersonInter, type Persons } from "../types/index";

// 定义一个变量person,必须符合PersonInter的接口规范
let person: PersonInter = {
  id: "0001",
  name: "张三",
  age: 18,
};

let personList1: Array<PersonInter> = [
  { id: "0001", name: "张三", age: 18 },
  { id: "0001", name: "张三", age: 18 },
  { id: "0001", name: "张三", age: 18 },
];

let personList2: Persons = [
  { id: "0001", name: "张三", age: 18 },
  { id: "0001", name: "张三", age: 18 },
  { id: "0001", name: "张三", age: 18 },
];
</script>

<template>
  <div class="person"></div>
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
