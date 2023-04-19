<template>
  <div class="movie-add-form">
    <form action="" class="add-form d-flex" @submit.prevent>
      <input
        type="text"
        class="form-control new-movie-label"
        placeholder="enter todo item"
        :value="name"
        @input="name = $event.target.value"
      />
      <button @click="addTodo" class="btn btn-outline-dark">Click</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
    };
  },

  methods: {
    addTodo() {
      const newTodo = {
        name: this.name,
        isCompleted: false,
        id: Date.now(),
      };
      this.$emit("createTodoItem", newTodo);
      this.name = "";
    },
  },
};
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
