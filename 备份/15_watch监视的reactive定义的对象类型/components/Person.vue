<script lang="ts" setup name="Person">
import { ObjectFlags } from "typescript";
import { ref, watch, reactive } from "vue";

let person = reactive({
  name: "张三",
  age: 18,
});

function changeName() {
  person.name += "~";
}
function changeAge() {
  person.age += 1;
}
function changePerson() {
  // reactive定义的数据的局限性，这样修改数据没有响应式
  // person = { name: "李四", age: 20 };
  // 这种形式实际上也没有改变person指向的地址，仅仅是键值对覆盖
  Object.assign(person, { name: "李四", age: 20 });
}

// 监视reactive定义的对象类型的数据是，默认是开启深度监听的，而且是不可以关闭深度监听的
watch(person, (newValue, oldValue) => {
  console.log("person改变了", newValue, oldValue);
});
</script>

<template>
  <div class="person">
    <h1>情况三：监视【reactive】定义的【对象类型】的数据</h1>
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
