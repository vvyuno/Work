<template>
  <ul v-if="todos.length > 0">
    <li v-for="todo in todos" :key="todo.id" class="flex gap-3 my-2">
      <button class="w-5 text-white bg-red-500" @click="deleteTodo(todo.id)">x</button>

      <button class="w-5 text-white bg-green-500" @click="completeTodo(todo.id)">o</button>

      <p :class="{ 'line-through': todo.complete }">{{ todo.text }}</p>
    </li>
  </ul>

  <p v-else>NO todos found.</p>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue'

defineProps({
  todos: {
    type: Array,
  },
})
const emit = defineEmits(['deleteTodo', 'completeTodo'])
const deleteTodo = (todoId) => {
  emit('deleteTodo', todoId)
}

const completeTodo = (todoId) => {
  emit('completeTodo', todoId)
}
</script>
