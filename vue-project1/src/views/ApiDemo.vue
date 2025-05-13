<template>
    <div>
        <button @click="increment">count：{{ count }}</button>
    </div>
</template>

<script setup>
// 1. 引入ref函数
import { ref, onMounted } from 'vue';

// 2. 声明一个响应式数据 count
const count = ref(0);

// 3.声明函数 - 在组合式API中没有this关键字
function increment() {
    count.value++;
}

// 4.钩子函数
onMounted(() => {
    console.log('Vue mounted...');
    
})
</script>

<style  scoped>

</style>