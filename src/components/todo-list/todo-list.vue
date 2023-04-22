<template>
  <ul class="movie-list list-group">
    <todoItem
      v-for="todo in Todos"
      :todo="todo"
      :key="todo.id"
      @remove="onDeleteHandler"
      @compeleted="onCompletedHandler"
    />
  </ul>
</template>

<script setup>
import todoItem from "../todo-item/todo-item.vue";
import { inject } from "vue";

const Todos = inject("Todos");

function onDeleteHandler(id) {
  Todos.value = Todos.value.filter((todo) => todo.id !== id);
}

function onCompletedHandler(id) {
  Todos.value.map((todo) => {
    if (todo.id == id) {
      todo.isCompleted = !todo.isCompleted;
    }
  });
}
</script>

<style>
.movie-list {
  margin-top: 2rem;
  margin-bottom: 1rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>
