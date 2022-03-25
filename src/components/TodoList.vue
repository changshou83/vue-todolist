<script setup>
import BinItem from '@/components/BinItem.vue';
import TodoItem from '@/components/TodoItem.vue';
import TodoFooter from '@/components/TodoFooter.vue';
import { ref, computed } from 'vue';

const currentTab = ref('main')

let id = 0;
const todos = ref([]);
const newTodo = ref(null)
todos.value.push({ id: id++, content: '完成编辑按钮', completed: false, deleted: false })
todos.value.push({ id: id++, content: '完成批量操作', completed: false, deleted: false })
const completedNumber = computed(() =>
  todos.value.filter(t => t.completed && !t.deleted).length
)

function addNew() {
  todos.value.push({ id: id++, content: newTodo.value, completed: false, deleted: false })
  newTodo.value = null
}
</script>

<template>
  <div class="container">
    <input
      type="text"
      placeholder="add new Todo"
      class="addInput"
      v-model="newTodo"
      @keyup.enter="addNew"
    />
    <input type="button" value="add" @click="addNew" />
    <div>
      <span :class="{ isActive: currentTab === 'main' }" @click="currentTab = 'main'">主面板</span>
      |
      <span :class="{ isActive: currentTab === 'bin' }" @click="currentTab = 'bin'">回收站</span>
    </div>
    <template v-for="(todo, index) in todos" :key="index">
      <TodoItem
        v-if="currentTab === 'main' && !todo.deleted"
        :todo="todo"
        @completeTodo="() => todo.completed = true"
        @deleteTodo="todo.deleted = true"
      />
      <BinItem
        v-if="currentTab === 'bin' && todo.deleted"
        :content="todo.content"
        @undo="todo.deleted = false"
      />
    </template>
    <TodoFooter :completedNumber="completedNumber" />
  </div>
</template>

<style scoped>
.addInput {
  margin: 20px 0;
}
.isActive {
  color: brown;
  background-color: black;
}
</style>
