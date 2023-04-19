<template>
  <div class="container">
    <todoAddForm @createTodoItem="createTodoItem" />
    <todoList
      :Todos="Todos"
      @onDelete="onDeleteHandler"
      @completed="isCompletedHandler"
    />
  </div>
</template>

<script>
import todoAddForm from "./components/todo-add-form/todo-add-form.vue";
import todoList from "./components/todo-list/todo-list.vue";
export default {
  components: {
    todoAddForm,
    todoList,
  },

  data() {
    return {
      Todos: [
        {
          name: "coding",
          isCompleted: false,
          id: 1,
        },
      ],
    };
  },

  mounted() {
    const storedTodos = localStorage.getItem("todos");
    if (storedTodos) {
      this.Todos = JSON.parse(storedTodos);
    }
  },

  methods: {
    createTodoItem(item) {
      this.Todos.push(item);
      localStorage.setItem("todos", JSON.stringify(this.Todos));
    },

    onDeleteHandler(id) {
      this.Todos = this.Todos.filter((todo) => todo.id != id);
      localStorage.setItem("todos", JSON.stringify(this.Todos));
    },

    isCompletedHandler(id) {
      this.Todos.map((todo) => {
        if (todo.id == id) {
          todo.isCompleted = !todo.isCompleted;
        }
      });
      localStorage.setItem("todos", JSON.stringify(this.Todos));
    },
  },
};
</script>
