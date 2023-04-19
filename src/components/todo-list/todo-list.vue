<template>
  <ul class="movie-list list-group">
    <todoItem
      v-for="todo in Todos"
      :todo="todo"
      @onDelete="$emit('onDelete', todo.id)"
      @completed="$emit('completed', todo.id)"
    />
  </ul>
</template>

<script>
import todoItem from "../todo-item/todo-item.vue";
export default {
  components: {
    todoItem,
  },
  data() {},

  props: {
    Todos: {
      type: Array,
      required: true,
    },
  },

  methods: {
    onDelete() {
      this.$emit("onDelete", todo.id);
    },
    completed() {
      this.$emit("completed", todo.id);
    },
  },
};
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
