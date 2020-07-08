<template>
  <div class="home">
    <v-container>
      <!-- Todo add -->
      <TodoAdd @onSubmit="addTask"/>
      <!-- Todo  List-->
      <TodoList :todos="todos | reversed" @onRemove="removeTask" />
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
      { id: 3, title: "Task 3", complete: false }
    ]
  }),
  computed: {
    reversedTodos() {
      return this.todos.slice().reverse()
    }
  },
  filters: {
    reversed(value) {
      return value.slice().reverse()
    }
  },
  methods: {
    async addTask(task) {
      let result = await axios.post('https://jsonplaceholder.typicode.com/todos', task)
      this.todos.push(result.data)
    },
    async removeTask(id) {
      await axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
};
</script>
