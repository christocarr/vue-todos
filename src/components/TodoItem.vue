<template>
  <div class="todo-container">
    <p>{{ todo.name }}</p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"]
}
</script>

<style scoped>
  .todo-container {
    display: flex;
    flex-direction: column;
    border: solid grey 1px;
  }
</style>