<script lang="ts">
import { registerRuntimeCompiler } from "vue";
export default {
  name: "Person",
  /* 
  从书写上来说，data(),methdos,setup()这些选项是可以同时用的，而且都可以生效
  那么，
  在data()中可以访问setup()中的属性或者函数吗 ： 可以
  在setup()中可以访问到data()中的属性吗 ： 不可以

  在methods中可以访问setup中的函数吗： 可以
  在setup中可以访问methods中的方法吗 ： 不可以

  原因大概是之前说过的setup的执行时机是最早的？？？

   */
  data() {
    return {
      a: 10,
      c: this.name, //访问setup中的name属性
      // 是可以访问到的，因为setup的执行时机是比beforeCreate：数据代理的创建，还要早的
    };
  },
  methods: {
    b() {
      console.log("bbbb");
    },

    f() {
      // methods中方法也是可以访问到setup中的属性的
      alert(this.age);
      // methods中方法也是可以访问到setup中定义的函数的
      this.showTel();
    },
  },
  setup() {
    let name = "张三";
    let age = 18;
    let tel = 17283344;
    // 想要访问data中的属性，这样直接报错，因为a在setup中是没有声明的：a is not defined
    // let x = a;

    function changeName() {
      name = "zhang-san";
    }
    function changeAge() {
      age += 1;
    }
    function showTel() {
      alert(tel);

      // 在setup函数总尝试使用data中的属性以及methods中的方法
      // alert(a) a is not defined
      // f(); f is not defined
    }

    return { name, age, tel, changeName, changeAge, showTel };
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
    <hr />
    <h2>测试setup和data(),methods</h2>
    <p>a:{{ a }}</p>
    <p>c:{{ c }}</p>
    <button @click="b">测试b方法</button>
    <button @click="f">测试f方法</button>
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
