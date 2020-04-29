<template>
  <div id="app">
    <Todos 
      v-bind:todos="todos" 
      v-on:delete-todo="deleteTodo"
    />
  </div>
</template>

<script>
import Todos from './components/Todos'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        {
          name: 'Todo One',
          isCompleted: false,
          id: 1
        },
        {
          name: 'Todo Two',
          isCompleted: false,
          id: 2
        },
        {
          name: 'Todo Three',
          isCompleted: false,
          id: 3
        }
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  },
  components: {
    Todos
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
    font-size: 18px;
  }
</style>
