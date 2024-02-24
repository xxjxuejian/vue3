<script lang="ts" setup name="Person">
import { ref, watch } from "vue";

let person = ref({
  name: "张三",
  age: 18,
});

function changeName() {
  person.value.name += "~";
}
function changeAge() {
  person.value.age += 1;
}
function changePerson() {
  person.value = { name: "李四", age: 20 };
}

/* 
1.监视的是对象类型的数据，整个对象的被修改了，可以监视到，
2. 如果想监视对象内部属性的变化，手动开启深度监听，{deep:true,immediate:true}立即执行一次监听函数
3. 如果修改的是整个对象，person.value={}的形式，newValue和oldValue不一样
4. 如果修改的是对象中的属性，person.value.name = xx,newValue和oldValue是一样的,地址指向的对象是一样的
*/
watch(
  person,
  (newValue, oldValue) => {
    console.log(newValue, oldValue);
  },
  { deep: true }
);
</script>

<template>
  <div class="person">
    <h1>情况二：监视【ref】定义的【对象类型】的数据</h1>
    <h2>姓名：{{ person.name }}</h2>
    <h2>年龄：{{ person.age }}</h2>
    <button @click="changeName">修改名字</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="changePerson">修改整个人</button>
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
