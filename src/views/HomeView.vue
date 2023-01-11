<script>
import { ref, onMounted, onUnmounted } from 'vue'
export default {
  setup() {
    // 所有的基础数据类型响应式都需要使用ref提供，并且读写的时候，需要使用value
    // 模板当中不需要的原因是，模板渲染函数中进行了处理
    const count = ref(10)

    // 在组件的mounted生命周期中执行函数
    onMounted(() => {
      console.log(count.value)
      setInterval(() => count.value--, 1000)
    })

    onUnmounted(() => {
      console.log('这个组件被销毁了')
    })

    // setup函数中，如果需要绑定至模板
    // 需要在setup函数中进行return
    return {
      count,
    }
  }
}
</script>

<template>
  <!-- 做了处理 -->
  <main>我就是想看看vue3的新特性{{ count }}</main>
</template>
