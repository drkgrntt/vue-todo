<template>
  <div>
    <form @submit="addTodo">
      <input type="text" v-model="title" name="title" placeholder="Add todo" />
      <input type="submit" value="Submit" class="button" />
    </form>
  </div>
</template>

<script>
// import { v4 } from 'uuid';

export default {
  name: "AddTodo",
  methods: {
    addTodo(event) {
      event.preventDefault()
      const newTodo = {
        // id: v4(),
        title: this.title,
        completed: false
      }
      // Send up to parent
      this.$emit('add-todo', newTodo);

      this.title = '';
    }
  },
  data() {
    return {
      title: ''
    }
  }
}
</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 5px;
  }

  input[type="submit"] {
    flex: 2;
  }
</style>