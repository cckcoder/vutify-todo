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
import axios from 'axios'

export default {
  name: "Home",
  async mounted() {
    let fetch_todos = await axios.get('https://jsonplaceholder.typicode.com/todos')
    this.todos = fetch_todos.data;
  },
  components: {
    TodoList,
    TodoAdd
  },
  data: () => ({
    todos: [],
    todos_mocup: [
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
