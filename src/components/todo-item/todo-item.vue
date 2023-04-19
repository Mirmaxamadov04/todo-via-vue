<template>
  <li
    class="list-group-item d-flex justify-content-between"
    :class="[{ completed: todo.isCompleted }]"
  >
    <span class="list-group-item-label">{{ todo.name }}</span>
    <div class="d-flex justify-content-center align-items-center">
      <button @click="completed" type="button" class="btn-cookie btn-sm">
        <i class="fas fa-cookie"></i>
      </button>
      <button @click="onDelete" type="button" class="btn-trash btn-sm">
        <i class="fas fa-trash"></i>
      </button>
    </div>
  </li>
</template>

<script>
export default {
  data() {
    return {};
  },

  props: {
    todo: {
      type: Object,
      required: true,
    },
  },

  methods: {
    onDelete() {
      this.$emit("onDelete", this.todo.id);
    },

    completed() {
      this.$emit("completed", this.todo.id);
    },
  },
};
</script>

<style scoped>
.list-group-item {
  padding: 15px 20px;
  border: none;
  border-bottom: 1px solid #3d5a80;
}

.list-group-item:last-child {
  border-bottom: none;
}

.list-group-item > span {
  line-height: 35px;
  font-size: 20px;
  cursor: pointer;
  width: 550px;
}

.list-group-item input {
  line-height: 35px;
  font-size: 20px;
  text-align: center;
  border: none;
  outline: none;
}

.list-group-item button {
  width: 35px;
  height: 35px;
  margin: 3px;
  font-size: 17px;
  border: none;
  cursor: pointer;
}

.list-group-item .btn-cookie {
  color: #e09f3e;
}

.list-group-item .btn-trash {
  color: #e5383b;
}

.list-group-item.completed .list-group-item-label,
.list-group-item.completed .list-group-item-input {
  opacity: 0.5;
  text-decoration: line-through;
}
</style>
