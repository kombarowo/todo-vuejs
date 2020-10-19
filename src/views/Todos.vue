<template>
  <div>
    <h2>Todo app</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <AddTodo
        v-on:add-todo="addTodo"
    />
    <hr>
    <Loader v-if="loading"/>
    <ToDoList
        v-else-if="todos.length"
        v-bind:todos="todos"
        v-on:remove-todo="removeTodo"
    />
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import ToDoList from '@/components/TodoList';
import AddTodo from '@/components/AddTodo';
import Loader from '@/components/Loader';

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=4')
        .then(response => response.json())
        .then(json => {
          setTimeout(() => {
            this.todos = json
            this.loading = false;
          }, 500);
        })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(item => item.id !== id);
    },
    addTodo(todo) {
      this.todos.push(todo);
    }
  },
  components: {
    Loader,
    AddTodo,
    ToDoList,
  }
}
</script>