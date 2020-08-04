<template>
  <div id="app">
    <!-- pass todos object as a prop named todoObj -->
    <Todos v-bind:todoObj='todos' v-on:del-todo='deleteTodo' />
  </div>
</template>

<script>
import Todos from './components/Todos';

export default {
  name: 'App',
  components: {
    Todos,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Todo One',
          completed: false,
        },
        {
          id: 2,
          title: 'Todo Two',
          completed: true,
        },
        {
          id: 3,
          title: 'Todo Three',
          completed: true,
        },
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todo = this.todo.filter(todo => todo.id !== id);
    }
  },
}
</script>

<style>
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
</style>
