<template>
  <div class="max-w-2xl mx-auto">
    <h1 class="text-red-500 font-bold text-lg underline">Hallo Dunia!</h1>
    <ul>
      <li
        v-for="todo of todos"
        :key="todo.id"
        class="py-2 px-4 my-4 bg-sky-200 rounded-md"
      >
        {{ todo.title }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Todo } from '~/interfaces'

export default {
  data() {
    return {
      todos: [] as Todo[],
    }
  },
  async fetch() {
    try {
      const response = await fetch(
        'https://jsonplaceholder.typicode.com/todos?_limit=10'
      )
      if (!response.ok) {
        throw new Error('Failed to fetch todos')
      }
      this.todos = await response.json()
    } catch (error) {
      // console.error('Error fetching todos:', error)
    }
  },
}
</script>
