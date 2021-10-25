<template>
  <div>
    <input type="text" v-model="todo.description">
    <button v-on:click="add()">Create Todo!</button>
  </div>
</template>

<script>
const initialTodo = () => {
  return { description: '', done: 0 }
}

export default {
  name: 'TodoCreate',
  data () {
    return { todo: initialTodo() }
  },
  methods: {
    add () {
      this.$emit('add-todo', this.todo)
      this.todo = initialTodo()
    }
  }
}
</script>
