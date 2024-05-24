<script setup>
import { ref, reactive } from 'vue'

// 给每个 todo 对象一个唯一的 id
let id = 0

const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

const myObject = reactive({
  title: 'How to do lists in Vue',
  author: 'Jane Doe',
  publishedAt: '2016-04-10'
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value });
  newTodo.value = ''
}

function removeTodo(idx) {
  console.log(idx);
  todos.value.splice(idx, 1);
}
</script>

<template>
  <ul>
    <!-- v-for = value, key, index in dict -->
    <li v-for="(value, key) in myObject">
      {{ value }} :{{ key }}
    </li>
  </ul>

  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo">
    <button>Add Todo</button>
  </form>
  <br>
  <ul>
    <!-- v-for = value, index in list -->
    <li v-for="(todo, index) in todos" :key="todo.id">
      {{ todo.id }} : {{ todo.text }}
      <button @click="removeTodo(index)">X</button>
    </li>
  </ul>
  
  <!-- idx从1开始 -->
  <span v-for="n in 10">{{ n }}</span>
</template>