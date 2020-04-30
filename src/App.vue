<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:delete-todo="deleteTodo" />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import AddTodo from './components/AddTodo';
import Todos from './components/Todos';

import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => {
          this.todos = this.todos.filter((todo) => todo.id !== id);
        })
        .catch((err) => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post('https://jsonplaceholder.typicode.com/todos', {
          title,
          completed,
        })
        .then((res) => (this.todos = [...this.todos, res.data]))
        .catch((err) => console.log(err));
    },
  },
  created() {
    axios
      .get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then((res) => (this.todos = res.data))
      .catch((err) => console.log(err));
  },
  components: {
    Header,
    AddTodo,
    Todos,
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
    Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  font-size: 18px;
}
</style>
