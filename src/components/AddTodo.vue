<template>
  <form @submit.prevent="addTodo">
    <input v-model="title" type="text" name="title" placeholder="Add todo" />
    <input type="submit" value="Add" class="button" />
  </form>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    addTodo() {
      const newTodo = {
        title: this.title,
        completed: false,
      };
      this.$emit('add-todo', newTodo);

      this.title = '';
    },
  },
};
</script>

<style scoped>
form {
  display: flex;
  height: 2rem;
}

form input[type='text'] {
  flex: 8;
  padding: 0.5rem;
  border: none;
}

.button {
  flex: 2;
}
</style>
