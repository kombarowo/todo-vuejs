<template>
  <form v-on:submit.prevent="onSubmit">
    <input type="text" v-model="title">
    <button>Add todo</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      title: ''
    }
  },
  methods: {
    onSubmit() {
      if (this.title !== '') {
        const newTodo = {
          id: Date.now(),
          title: this.title,
          completed: false
        }

        this.$emit('add-todo', newTodo);
        this.title = '';
      }
    }
  }
}
</script>

<style scoped>
form {
  max-width: 500px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
}

input {
  padding: 0.5rem 1rem;
  width: 350px;
}

button {
  font-weight: 700;
}
</style>