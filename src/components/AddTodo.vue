<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add Todo...">
      <input type="submit" value="submit" class="btn">
    </form>
  </div>
</template>

<script>
// import { v4 as uuidv4 } from 'uuid';

export default {
  name: 'AddTodo',
  data() {
    return {
      title: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      // json placeholder has it own id, so we no longer need uuid
      const newTodo = {
        // id: uuidv4(),
        title: this.title,
        completed: false,
      }
      // send up to parent
      this.$emit('add-todo', newTodo)
      this.title = '';
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type='text'] {
    flex: 10;
    padding: 5px;
  }

  input[type='submit'] {
    flex: 2;
  }
</style>