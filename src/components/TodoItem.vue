<template>
  <div>
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

</style>