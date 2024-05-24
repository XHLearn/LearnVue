<script setup>
import { ref } from 'vue'

// 给每个 todo 对象一个唯一的 id
let id = 0

const newTodo = ref('')
const todos = ref([
  { id: id++, text: 'Learn HTML' },
  { id: id++, text: 'Learn JavaScript' },
  { id: id++, text: 'Learn Vue' }
])

function addTodo() {
  todos.value.push({id:id++, text:newTodo.value});
  newTodo.value = ''
}

function removeTodo(idx) {
  console.log(idx);
  todos.value.splice(idx, 1);
}
</script>

<template>
  <form @submit.prevent="addTodo">
    <input v-model="newTodo" required placeholder="new todo">
    <button>Add Todo</button>
  </form>
  <br>
  <ul>
    <li v-for="(todo, index) in todos" :key="todo.id">
      {{ todo.id }} : {{ todo.text }}
      <button @click="removeTodo(index)">X</button>
    </li>
  </ul>
</template>