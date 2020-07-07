<template>
  <div class="home">
    <v-container>
      <!-- Todo add -->
      <TodoAdd @onSubmit="addTask"/>
      <!-- Todo  List-->
      <TodoList :todos="todos" @onRemove="removeTask" />
      <v-row class="d-flex justify-center">
        <img src="@/assets/logo.png" alt="" class="mt-5">
      </v-row>
      <v-img src="@/assets/logo.png"
        contain
        max-height="200"/>
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
      { id: 1, title: "Task 1", complete: true },
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
