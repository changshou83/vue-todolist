<script setup>
defineProps(['content'])
defineEmits(['undo'])
</script>

<template>
  <div>
    <span>{{ content }}</span>
    <input type="button" value="撤销" class="completeBtn" @click="$emit('undo')" />
  </div>
</template>

<style scoped>
</style>