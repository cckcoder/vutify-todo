<template>
      <v-card>
        <v-card-title primary-title>
          <v-container>
            <v-row
              class="d-flex flex-row align-center"
              v-for="(todo, index) in todos"
              :key="index"
            >
              <v-col cols="12" class="d-flex flex-row align-center pa-0">
              <v-checkbox class="mr-3" v-model="value" value="value"></v-checkbox>
              <span>{{ todo.title }}</span>
              <v-spacer></v-spacer>
              <v-btn @click="$emit('onRemove', todo.id)" color="error">X</v-btn>
              </v-col>
              <v-col cols="12">
              <v-divider></v-divider>
              </v-col>
            </v-row>
          </v-container>
        </v-card-title>
      </v-card>
</template>

<script>
export default {
  name: "TodoList",
  props: ["todos"]
}
</script>

<style>

</style>
