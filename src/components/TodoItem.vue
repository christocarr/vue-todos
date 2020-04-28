<template>
  <div class="todo-container" v-bind:class="{'is-complete':todo.isCompleted}">
    <p>
      <input type="checkbox" v-on:change="makeComplete">
      {{ todo.name }}
      <button class="delete-button">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
    methods: {
    makeComplete() {
      this.todo.isCompleted = !this.todo.isCompleted
    }
  }
}
</script>

<style scoped>
  .todo-container {
    padding: 0.5rem;
    border-bottom: solid grey 1px;
    background-color: lightblue;
  }

  .is-complete {
    text-decoration: line-through;
  }

  .delete-button {
    width: 3rem;
    height: 2rem;
  }
</style>