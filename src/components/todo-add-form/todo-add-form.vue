<template>
  <div class="movie-add-form">
    <form action="" class="add-form d-flex" @submit.prevent>
      <input
        type="text"
        class="form-control new-movie-label"
        placeholder="enter todo item"
        :value="newTask"
        @input="newTask = $event.target.value"
      />
      <button class="btn btn-outline-dark" @click="addNewTodo">Click</button>
    </form>
  </div>
</template>

<script setup>
import { ref, inject } from "vue";

const newTask = ref("");
const Todos = inject("Todos");

function addNewTodo() {
  if (newTask.value.length == 0) {
    return false;
  }
  const newTodo = {
    id: Date.now(),
    task: newTask.value,
    isCompleted: false,
  };

  Todos.value.push(newTodo);
  newTask.value = "";
  localStorage.setItem("todos", JSON.stringify(Todos.value));
}
</script>

<style>
.movie-add-form {
  margin-top: 2rem;
  margin-bottom: 1rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>
