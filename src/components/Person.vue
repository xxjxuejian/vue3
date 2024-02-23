<script lang="ts" setup name="Person">
import { reactive, toRefs } from "vue";

let person = reactive({
  name: "张三",
  age: 20,
});

/* 
  从一个响应式对象中解构出的属性，不具备响应式,如果希望具有响应式，就使用toRefs()
  这时候name,age就变成了使用ref定义的变量
  toRefs(person): {name: ObjectRefImpl, age: ObjectRefImpl}
  把person对象中的每一组key和value都做处理 
  {
    name：ref(person.name)
    age: ref(person.age)
  }
  实际上的源头时person.name和person.age
  修改person.age, age变化
  修改age，实际就是修改person.age
*/
let { name, age } = toRefs(person);

function changeName() {
  name.value += "~";
}
function changeAge() {
  age.value += 1;
}

function changeAge2() {
  person.age += 1;
}

console.log(person);
console.log(toRefs(person));
console.log(name);
console.log(age);
</script>

<template>
  <div class="person">
    <h2>姓名：{{ name }}</h2>
    <h2>年龄：{{ age }}</h2>
    <h2>年龄{{ person.age }}</h2>
    <button @click="changeName">修改姓名</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="changeAge2">修改person的年龄</button>
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
