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
      todos: [
        {id: 1, title: 'Проснуться', completed: false},
        {id: 2, title: 'Умыться', completed: false},
        {id: 3, title: 'Поесть', completed: false},
        {id: 4, title: 'Лечь спать', completed: false},
      ]
    }
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
