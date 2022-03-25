<script setup>
defineProps(['todo'])
defineEmits(['completeTodo', 'deleteTodo'])
</script>

<template>
  <div class="container">
    <div :class="[{ isCompleted: todo.completed }, 'content']">{{ todo.content }}</div>
    <div class="btn">
      <input type="button" value="√" class="completeBtn" @click="$emit('completeTodo')" />
      <input type="button" value="x" class="deleteBtn" @click="$emit('deleteTodo')" />
      <input type="button" value="E" class="editBtn" @click="$emit('editTodo')" />
    </div>
  </div>
</template>

<style scoped>
.container {
  width: 500px;
  position: relative;
  left: calc(50% - 250px);

  margin: 8px 0;

  border: solid 2px rgb(0, 119, 255);

  display: flex;
}

.btn {
  flex: 1;
  display: flex;
  border: 0;
}

.completeBtn,
.deleteBtn,
.editBtn {
  color: #fff;
  flex: 1;
  transition: flex 0.5s cubic-bezier(0.165, 0.84, 0.44, 1);
}
.completeBtn:hover,
.deleteBtn:hover,
.editBtn:hover {
  flex: 10;
  transition: flex 2s cubic-bezier(0.165, 0.84, 0.44, 1);
}
.completeBtn {
  background-color: rgb(255, 158, 47);
}

.deleteBtn {
  background-color: red;
}
.editBtn {
  background-color: rgb(0, 119, 255);
}
.isCompleted {
  text-decoration: line-through;
}

.content {
  width: 400px;
  box-sizing: border-box;
  padding: 10px 12px;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: hidden;
  background-color: #eee;
}
</style>