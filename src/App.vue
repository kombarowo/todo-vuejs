<template>
  <div id="app">
    <h1>Todo app</h1>
    <AddTodo
        v-on:add-todo="addTodo"
    />
    <hr>
    <ToDoList
        v-bind:todos="todos"
        v-on:remove-todo="removeTodo"
    />
  </div>
</template>

<script>
import ToDoList from '@/components/TodoList';
import AddTodo from '@/components/AddTodo';

export default {
  name: 'App',
  data() {
    return {
      todos: []
    }
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
        .then(response => response.json())
        .then(json => this.todos = json)
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
    AddTodo,
    ToDoList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
