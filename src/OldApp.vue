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
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: [],
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => this.todos = this.todos.filter(todo => todo.id !==id))
        .catch(err => console.log(err))
      // this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed,
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
    },
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
  }
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
