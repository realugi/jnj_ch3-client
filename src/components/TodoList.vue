<template>
  <div>
    <todo-element
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:description="todo.description"
      v-bind:done="todo.done"
    ></todo-element>
  </div>
</template>

<script>
import TodoElement from '@/components/TodoElement'

export default {
  name: 'TodoList',
  components: {
    'todo-element': TodoElement
  },
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
