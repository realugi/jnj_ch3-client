<template>
  <div>
    <input type="text" v-model="todo.description">
    <button v-on:click="add()">Create Todo!</button>
  </div>
</template>

<script>
export default {
  name: 'TodoCreate',
  data () {
    return {
      todo: {description: '', done: 0}
    }
  },
  methods: {
    add () {
      this.$emit('add-todo', this.todo)
    }
  }
}
</script>
