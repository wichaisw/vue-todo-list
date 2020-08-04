<template>
  <div>
    <!-- v-bind:key กำหนด key ให้ loop element เหมือน react -->
    <!-- v-for ใช้ loop array ของ object todoObj -->
    <div v-bind:key='todo.id' v-for='todo in todoObj'>
      <!-- <h3>{{todo.title}}</h3> -->
      <TodoItem v-bind:todo='todo' v-on:del-todo='$emit("del-todo", todo.id)' />
    </div>
  </div>
</template>

<script>
import TodoItem from './TodoItem';

export default {
  name: 'Todos',
  components: {
    TodoItem,
  },
  props: ['todoObj']
}
</script>

<style scoped>
  
</style>