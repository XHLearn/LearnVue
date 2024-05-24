<script setup>
import { ref, onMounted } from 'vue'

// 响应式状态
const count = ref(4);
const isSpanDisable = true;

// 用来修改状态、触发更新的函数
function increment() {
  count.value++;
  if(count.value % 2 === 0){
    isSpanDisable = true;
  } else {
    isSpanDisable = false;
  }
}

// 生命周期钩子
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">CountAdd</button>
  <span :disabled="isSpanDisable"> count: {{ count }}</span>
</template>