<script lang="ts" setup name="Person">
import { ref, computed } from "vue";

let firstName = ref("张");
let lastName = ref("三");

/*
计算属性的特点，只要它依赖的数据发生变化以后，就会重新计算，如果页面中多次用到同一个计算属性，
只有第一次会调用计算属性，后续就被缓存了，直接拿来用。
但是方法就不会缓存
*/

// 这种定义的计算属性是只读的，不可以修改，
/* let fullName = computed(() => {
  console.log("计算属性被调用");
  return firstName.value + lastName.value;
}); */

// 这样的计算属性是可读可写的,设置get和set方法
let fullName = computed({
  get() {
    return firstName.value + "-" + lastName.value;
  },
  set(v) {
    // 拿到新的值，分别修改它所依赖的数据
    let [f, l] = v.split("-");
    firstName.value = f;
    lastName.value = l;
  },
});

// 计算属性也是一个ref定义出来的响应式数据，访问需要使用.value
function changeFullName() {
  fullName.value = "li-si";
}
</script>

<template>
  <div class="person">
    姓：<input type="text" v-model="firstName" /> <br />
    名：<input type="text" v-model="lastName" /> <br />
    <button @click="changeFullName">修改fullName</button> <br />
    <!-- 计算属性用了三次，但是只有第一次的时候才调用了computed(),后面用的是缓存 -->
    全名：<span>{{ fullName }}</span> <br />
    全名：<span>{{ fullName }}</span> <br />
    全名：<span>{{ fullName }}</span> <br />
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
