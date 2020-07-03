<template>
  <div class="home">
    <v-container>
      <v-row >
        <v-col cols="10">
          <v-text-field name="name" label="Task" id="id">
          </v-text-field>
        </v-col>

        <v-col cols="2">
          <v-btn block color="success">Add</v-btn>
        </v-col>
      </v-row>
      <v-card>
        <v-card-title primary-title>
          <v-container>
            <v-row
              class="d-flex flex-row align-center"
              v-for="(todo, index) in todos"
              :key="index"
            >
              <v-col cols="12" class="d-flex flex-row align-center">
              <v-checkbox v-model="value" value="value"></v-checkbox>
              <span>{{ todo.title }}</span>
              <v-spacer></v-spacer>
              <v-btn color="error">X</v-btn>
              </v-col>
              <v-col cols="12">
              <v-divider></v-divider>
              </v-col>
            </v-row>
          </v-container>
        </v-card-title>
      </v-card>
    </v-container>
  </div>
</template>

<script>

export default {
  name: "Home",
  components: {
  },
  data: () => ({
    todos: [
      { id: 1, title: "Task 1", complete: false },
      { id: 2, title: "Task 2", complete: true },
      { id: 3, title: "Task 3", complete: false },
      { id: 4, title: "Task 4", complete: true }
    ]
  })
};
</script>
