<template>
  <v-row>
    <v-col cols="10">
      <v-text-field
        name="name"
        label="Task"
        id="id"
        v-model="taskTextField"
        @keyup.enter="addTask">
      </v-text-field>
    </v-col>

    <v-col cols="2">
      <v-btn block color="success" @click="addTask">Add</v-btn>
    </v-col>
  </v-row>
</template>

<script>
import { v4 as uuidv4 } from 'uuid'

export default {
  name: "TodoAdd",
  data: () => ({
    taskTextField: ""
  }),
  methods: {
    addTask() {

      let task = {
        id: uuidv4(),
        title: this.taskTextField,
        complete: false
      }

      this.$emit('onSubmit', task)
      this.taskTextField = ""
    }
  }
}
</script>

<style>

</style>
