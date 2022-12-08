<template>
  <div class="right-container">
    <h3>Right 组件 --- rightCount: {{ rightCount }}</h3>
    <button @click="addRightCount">rightCount + 1</button>
    <span>收到Left发来的消息: {{ RightMsg }}</span>
    <hr>
    <!-- 父向子传值 -->
    <MyCount :init="6"></MyCount>
  </div>
</template>

<script>
import bus from './EventBus.js'
export default {
  data() {
    return {
      rightCount: 0,
      RightMsg: ''
    }
  },
  created() {
    // 接收left发送的消息
    bus.$on('share', (val) => {
      console.log('Right接收到Left发来的消息', val);
      this.RightMsg = val
    })
  },
  methods: {
    addRightCount() {
      this.rightCount ++
      // 子向父传值，通过$emit()触发自定义事件
      this.$emit('numChange', this.rightCount)
    }
  }

}
</script>

<style lang="less">
.right-container {
  padding: 0 20px 20px;
  background-color: lightskyblue;
  min-height: 250px;
  flex: 1;
}
</style>
