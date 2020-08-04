<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo='addTodo' />
    <!-- pass todos object as a prop named todoObj -->
    <Todos v-bind:todoObj='todos' v-on:del-todo='deleteTodo' />
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
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
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
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

  .btn {
    display: inline-block;
    border: none;
    background: #555555;
    color: #ffffff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666666;
  }
</style>
