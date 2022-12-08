<template>
  <div>
    <span>{{ arr }}</span>
    <button @click="arrFor">arrFor</button>
    <button @click="arrAllChoose">是否被全选</button>
    <button @click="arrReduce">已勾选的水果计算总价格</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      arr: [
        { id: 1, name: "西瓜", status: true, price: 10, count: 20 },
        { id: 2, name: "苹果", status: true, price: 8, count: 80 },
        { id: 3, name: "芒果", status: false, price: 20, count: 10 },
        { id: 4, name: "榴莲", status: true, price: 200, count: 1 },
      ],
    };
  },
  methods: {
    arrFor() {
      // forEach不能中止循环
      // this.arr.forEach((item, index) => {
      //   console.log(index);
      //   if (item.name === '苹果') {
      //     console.log(index);
      //   }
      // })

      // some可以通过return true 终止循环
      this.arr.some((item, index) => {
        console.log(index);
        if (item.name === "苹果") {
          console.log(index);
          return true;
        }
      });
    },
    arrAllChoose() {
      // item.status是否全部为true
      const result = this.arr.every((item) => item.status);
      console.log(result);
    },
    arrReduce() {
      // this.arr.filter(item => item.status).reduce((累加的结果, 当前循环项) => {
      //  return 累加的结果; // return的值会放到   累加的结果↑  继续下一次循环
      // }, 初始值)

      // const result = this.arr
      //   .filter((item) => item.status)
      //   .reduce((amt, item) => {
      //     return (amt += item.price * item.count);
      //   }, 0);
      // 简写形式
      const result = this.arr
        .filter((item) => item.status)
        .reduce((amt, item) => (amt += item.price * item.count), 0);
      console.log(result);
    },
  },
};
</script>

<style>
</style>