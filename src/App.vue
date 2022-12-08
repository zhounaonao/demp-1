<template>
  <div class="app-container">
    <h1>App 根组件 --- rightCount: {{ rightCount }}</h1>
    <button @click="reLeftMsg">更改left组件的leftMsg</button>
    <Test :init="10" v-if="isTest"></Test>
    <button @click="isTest = !isTest">Test组件的展开和关闭</button>
    <hr />
    <!-- @blur失去焦点触发事件 -->
    <input ref="iptRef" v-if="showIB" @blur="showButton" type="text" />
    <button v-else @click="showInput">显示输入框</button>
    <hr />
    <div class="box">
      <!-- 渲染 Left 组件和 Right 组件 -->
      <Left ref="comLeft"></Left>
      <Right @numChange="getNewRightCount"></Right>
    </div>
  </div>
</template>

<script>
import Left from "@/components/Left.vue";
import Right from "@/components/Right.vue";
import Test from "@/components/Test.vue";
export default {
  components: {
    Left,
    Right,
    Test,
  },
  data() {
    return {
      isTest: true,
      rightCount: 0,
      showIB: false,
    };
  },
  methods: {
    getNewRightCount(rightCount) {
      this.rightCount = rightCount;
    },
    reLeftMsg() {
      console.log(this);
      this.$refs.comLeft.leftMsg = "我是App，我使用$refs更改了Left组件的消息";
    },
    showInput() {
      this.showIB = true;
      // 让input自动获取焦点
      // Cannot read properties of undefined (reading 'focus')
      // 直接调用会报这个错误，iptRef是undefined的
      // 因为使用v-if的时候还没渲染
      // this.$refs.iptRef.focus();
      // 需要我们使用this.$nextTick()方法等到dom重新渲染后执行
      this.$nextTick(() => {
        this.$refs.iptRef.focus();
      })
    },
    showButton() {
      this.showIB = false;
    },
  },
};
</script>

<style lang="less">
.app-container {
  padding: 1px 20px 20px;
  background-color: #efefef;
}
.box {
  display: flex;
}
</style>
