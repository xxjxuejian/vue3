<script lang="ts">
// setup也是一个选项，是一个函数
export default {
  name: "Person",
  beforeCreate() {
    console.log("beforeCreate执行了！！！");
  },
  setup() {
    // setup执行时间在beforeCreate之前
    console.log("setup执行了！！！");

    // 数据
    // 在setup中使用这种方法定义的数据是没有响应式的
    let name = "张三";
    let age = 18;
    let tel = 17283344;

    // 方法,在setup选项中的方法中是没有this的
    // 这样修改的数据页面并不会变化
    function changeName() {
      name = "zhang-san";
    }
    function changeAge() {
      age += 1;
    }
    function showTel() {
      alert(tel);
    }

    // 返回的数据或者方法，才能在模板中使用的
    return {
      name,
      age,
      tel,
      changeName,
      changeAge,
      showTel,
    };
  },
};
</script>

<template>
  <div class="person">
    <h2>姓名{{ name }}</h2>
    <h2>年龄{{ age }}</h2>
    <button @click="changeName">修改姓名</button>
    <button @click="changeAge">修改年龄</button>
    <button @click="showTel">查看联系方式</button>
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
