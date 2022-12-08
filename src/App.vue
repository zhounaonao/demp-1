<template>
  <div class="app-container">
    <h1>App 根组件 --- rightCount: {{ rightCount }}</h1>
    <Test :init="10" v-if="isTest"></Test>
    <button @click="(isTest = !isTest)">Test组件的展开和关闭</button>
    <hr />

    <div class="box">
      <!-- 渲染 Left 组件和 Right 组件 -->
      <Left></Left>
      <Right @numChange="getNewRightCount"></Right>
      
    </div>
  </div>
</template>

<script>
import Left from '@/components/Left.vue'
import Right from '@/components/Right.vue'
import Test from '@/components/Test.vue'
export default {
  components: {
    Left, Right, Test
  },
  data() {
    return {
      isTest: true,
      rightCount: 0
    }
  },
  methods: {
    getNewRightCount(rightCount) {
      this.rightCount = rightCount
    }
  }


}
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
