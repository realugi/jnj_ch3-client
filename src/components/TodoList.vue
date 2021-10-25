<template>
  <p>Hello World!</p>
</template>

<script>
export default {
  name: 'TodoList',
  data () {
    return {
      todos: []
    }
  },
  created () {
    var todoApi = this.$resource('todos{/id}')
    todoApi.get().then(res => {
      this.todos = res.body
    })
  }
}
</script>
