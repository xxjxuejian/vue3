<script lang="ts">
// 选项式Api的缺点是，一个需求的数据和方法等分布在data,methods中，不集中，不便于维护和复用
// 新增需求就要分别在这些选项中修改代码
// vue3的组合式APi的代码就比较集中
export default {
  name: "Person",
  data() {
    return {
      name: "张三",
      age: 18,
      tel: 19223243242,
    };
  },
  methods: {
    showTel() {
      alert(this.tel);
    },
    changeName() {
      this.name = "zhang-san";
    },
    changeAge() {
      this.age += 1;
    },
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
