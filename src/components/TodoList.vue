<template>
  <div>
    <todo-element
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:todo="todo"
      v-on:update-todo="$emit('update-todo', $event)"
      v-on:delete-todo="$emit('delete-todo', $event)"
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
  props: ['todos']
}
</script>
