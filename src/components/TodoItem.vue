<template>
  <div class="todo-container" v-bind:class="{'is-complete':todo.completed}">
    <p>
      <input type="checkbox" v-on:change="makeComplete">
      {{ todo.title }}
      <button 
        class="delete-button" 
        @click="$emit('delete-todo', todo.id)">
        x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
    methods: {
    makeComplete() {
      this.todo.completed = !this.todo.completed
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
    float: right;
    height: 1.5rem;
  }
</style>