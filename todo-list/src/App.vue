<script setup>
import AddTodo from './components/AddTodo.vue'
import TodoList from './components/TodoList.vue'
import { ref } from 'vue'

const todos = ref([
  {
    id: 1,
    text: 'Test',
  },
])

const handleAddTodo = (todo) => {
  todos.value.push(todo)
}

const handleDeletTodo = (todoId) => {
  todos.value = todos.value.filter((todo) => todo.id !== todoId)
}

const handlCompleteTodo = (todoId) => {
  todos.value = todos.value.map((todo) =>
    todo.id !== todoId ? { ...todo, complete: !todo.complete } : todo,
  )
}
</script>

<template>
  <div class="flex justify-center min-h-[100vh] items-center flex-col">
    <AddTodo @add-Todo="handleAddTodo" />
    <TodoList :todos="todos" @delete-todo="handleDeletTodo" @complete-todo="handlCompleteTodo" />
  </div>
</template>
