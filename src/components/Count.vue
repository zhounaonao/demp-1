<template>
  <div>
    <h5>Count组件</h5>
    <p>count 的值是: {{ count }}</p>
    <button @click="count++">count+1</button>
  </div>
</template>

<script>
export default {
    // 自定义组件属性，为当前组件指定初始值，不建议直接修改props的数据
    // props: ['init'],
    props: {
        // 自定义属性: {配置选项}
        init: {
            default: 0, // 默认值
            type: Number, // 不符合这个类型就会报错
            required: true // true就是必填项
        }
    },
    data() {
        return {
            count: this.init
        }
    },
    methods: {

    }
}
</script>

<style lang="less">

</style>