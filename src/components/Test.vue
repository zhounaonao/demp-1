<template>
  <div>
    <h3>Test组件</h3>
  </div>
</template>

<script>

export default {
    props: ['init'],
    data() {
        return {
            username: 'Test'
        }
    },
    methods: {
        show() {
            console.log('show');
        }   
    },
    beforeCreate() {
        // 创建之前，下面都处于不可用状态
        // console.log(this.init);
        // console.log(this.username);
        // this.show()
    },
    // 重要
    created() {
        // 创建完成后，下面都可以使用，模板结构暂未生成，不能操作dom 
        console.log(this.init);
        console.log(this.username);
        this.show()
    },
    beforeMount() {
        // 编译好的HTML结构存在内存里
    },
    // 重要
    mounted() {
        // 已经把内存中的HTML结构，成功的渲染到了浏览器之中，可以操作dom了(最早)，创建阶段结束了
        console.log(this.$el);
    },
    // 创建阶段结束
    // 组件运行阶段
    beforeUpdate() {
        // 数据改变的时候触发
        console.log('beforeUpdate');
    },
    // 重要
    updated() {
        // 更新数据渲染完成，操作最新的dom

    },
    // 组件销毁阶段
    beforeDestroy() {
        // 组件销毁前触发
        console.log('beforeDestory');
    },
    destroyed() {
        // 组件已经被销毁完成
        console.log('destoryed');
    }

}
</script>

<style>

</style>