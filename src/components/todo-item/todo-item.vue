<template>
  <li
    class="list-group-item d-flex justify-content-between"
    :class="[{ completed: todo.isCompleted }]"
    :id="todo.id"
  >
    <span class="list-group-item-label">{{ todo.task }}</span>
    <div class="d-flex justify-content-center align-items-center">
      <button type="button" class="btn-cookie btn-sm" @click="onCompeted">
        <i class="fas fa-cookie"></i>
      </button>
      <button type="button" class="btn-trash btn-sm" @click="onDelete">
        <i class="fas fa-trash"></i>
      </button>
    </div>
  </li>
</template>

<script setup>
const props = defineProps(["todo"]);
const emits = defineEmits(["remove"], ["compeleted"]);

function onDelete() {
  emits("remove", props.todo.id);
}

function onCompeted() {
  emits("compeleted", props.todo.id);
}
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
