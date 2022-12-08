<template>
  <div data-v-001 class="left-container">
    <h3 data-v-001>Left 组件</h3>
    <button @click="sendMsg">发送消息给Right</button>
    <span>将要发送的消息：{{ leftMsg }}</span>
    <hr>
    <h4 data-v-001>data-v-001</h4>
    <!-- :后成为数值9，不然是字符串9 -->
    <MyCount :init="9"></MyCount>
  </div>
</template>

<script>
import bus from './EventBus.js'
export default {
  data() {
    return {
      leftMsg: 'left将要发给right的消息'
    }
  },
  methods: {
    sendMsg() {
      // 用$emit方法将数据发送给EventBus
      bus.$emit('share', this.leftMsg)
    }
  }

}
</script>

<!-- 样式默认是全局的（样式冲突）加上样式属性就能避免样式冲突
  加完scoped就相当于加了样式属性['data-v-xxxxx'] 就不会出现样式冲突-->
<style lang="less" scoped>
.left-container {
  padding: 0 20px 20px;
  background-color: orange;
  min-height: 250px;
  flex: 1;
}
h3 {
  color: red;
}
h4[data-v-001] {
  color: green;
}
// 父组件中直接改子组件的样式
// [data-v-3c83f0b7] h5
/deep/ h5 {
  color: blue;
}
</style>
