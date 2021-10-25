<template>
  <div>
    <p>id: {{ todo.id }}</p>
    <p>description: {{ todo.description }}</p>
    <p>done: {{ todo.done === 0 ? 'no' : 'yes' }}</p>
    <button v-on:click="check()">Check</button>
    <button v-on:click="uncheck()">Uncheck</button>
    <button v-on:click="remove()">Delete</button>
  </div>
</template>

<script>
export default {
  name: 'TodoElement',
  props: ['todo'],
  methods: {
    check () {
      const todo = { ...this.todo }
      todo.done = 1
      this.$emit('update-todo', todo)
    },
    uncheck () {
      const todo = { ...this.todo }
      todo.done = 0
      this.$emit('update-todo', todo)
    },
    remove () {
      this.$emit('delete-todo', this.todo)
    }
  }
}
</script>
