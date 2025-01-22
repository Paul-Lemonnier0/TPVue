<script setup lang="ts">
import TodoItem from '@/components/TodoItem.vue'
import type Todo from '@/models/Todo'
import { reactive } from 'vue'

// Initialisation des todos dans un tableau réactif
const todos = reactive<Todo[]>([
  {
    id: 1,
    title: 'Learn Vue 3',
    completed: false,
  },
  {
    id: 2,
    title: 'Learn Vite',
    completed: false,
  },
  {
    id: 3,
    title: 'Learn Vue Router',
    completed: false,
  },
  {
    id: 4,
    title: 'Learn Vuex',
    completed: false,
  },
])

// Fonction pour marquer les tâches comme terminées
const toggleTodo = (id: number) => {
  const todo = todos.find((todo) => todo.id === id)
  if (todo) {
    todo.completed = !todo.completed
  }
}
</script>

<template>
  <main>
    <div class="todoList">
      <h2>My Todo List</h2>
      <ul>
        <!-- Affichage des tâches -->
        <li v-for="todo in todos" :key="todo.id" :class="{ completed: todo.completed }">
          <TodoItem
            :title="todo.title"
            :subTitle="todo.completed ? 'Completed' : 'Pending'"
            :is-checked="todo.completed"
            @handle-on-press="() => toggleTodo(todo.id)"
          />
        </li>
      </ul>
    </div>
  </main>
</template>

<style scoped>
.todoList {
  margin-top: 2rem;
  font-size: 1rem;
}

.todoList ul {
  list-style-type: none;
  padding: 0;
}

.todoList li {
  display: flex;
  align-items: center;
  margin: 10px 0;
}

.completed {
  text-decoration: line-through;
  color: gray;
}
</style>
