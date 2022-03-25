<script setup>
defineProps(['completedNumber'])
</script>

<template>
  <div class="container">
    <div>completed:{{ completedNumber }}</div>
  </div>
</template>

<style scoped>
.container {
  width: 500px;
  position: relative;
  left: calc(50% - 250px);

  margin: 12px 0;
  padding: 10px 0;

  color: rgb(124, 238, 143);
  border: solid 2px rgb(124, 238, 143);
}
</style>