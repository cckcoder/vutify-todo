<template>
  <div class="home">
    <v-container>
      <!-- Todo add -->
      <TodoAdd @onSubmit="addTask"/>
      <!-- Todo  List-->
      <TodoList :todos="todos" @onRemove="removeTask" />
    </v-container>
  </div>
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import TodoAdd from '@/components/TodoAdd.vue'

export default {
  name: "Home",
  components: {
    TodoList,
    TodoAdd
  },
  data: () => ({
    todos: [
      { id: 1, title: "Task 1", complete: false },
      { id: 2, title: "Task 2", complete: true },
      { id: 3, title: "Task 3", complete: false },
    ]
  }),
  methods: {
    addTask(task) {
      this.todos.push(task)
    },
    removeTask(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
};
</script>
