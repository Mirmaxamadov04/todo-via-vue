<template>
  <div class="container">
    <todoAddForm />
    <todoList :Todos="Todos" />
  </div>
</template>

<script setup>
import todoAddForm from "./components/todo-add-form/todo-add-form.vue";
import todoList from "./components/todo-list/todo-list.vue";
import { ref, provide, watch } from "vue";

const storedTodos = JSON.parse(localStorage.getItem("todos"));

const Todos = ref(
  storedTodos || [
    {
      id: 1,
      task: "coding",
      isCompleted: false,
    },
  ]
);

function createNewTodo() {
  localStorage.setItem("todos", JSON.stringify(Todos.value));
}

provide("Todos", Todos);
watch(Todos, createNewTodo, { deep: true });
</script>
