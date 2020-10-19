<template>
  <li>
    <span v-bind:class="{done: todo.completed}">
      <input
          type="checkbox"
          v-on:change="todo.completed = !todo.completed ">
      <strong>{{ index + 1 }}</strong>
      {{ todo.title }}
    </span>
    <button class="remove"
            v-on:click="$emit('remove-todo',todo.id)"
    >&times;
    </button>
  </li>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    },
    index: {
      type: Number,
      required: true
    }
  }
}
</script>

<style scoped>
li {
  border: 1px solid gray;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.5rem 1rem;
  margin-bottom: 1rem;
}

input {
  margin-right: 1rem;
}

.remove {
  background: red;
  border: none;
  font-weight: 700;
  border-radius: 50%;
  color: #fff;
}

.done {
  text-decoration: line-through;
}

.remove:active, .remove:focus {
  outline: none;
}
</style>