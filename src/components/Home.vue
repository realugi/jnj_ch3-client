<template>
  <div>
    <todo-create v-on:add-todo="addTodo"></todo-create>
    <todo-element
      v-for="todo in todos"
      v-bind:key="todo.id"
      v-bind:todo="todo"
      v-on:update-todo="updateTodo"
      v-on:delete-todo="deleteTodo"
    ></todo-element>
  </div>
</template>

<script>
import TodoElement from '@/components/TodoElement'
import TodoCreate from '@/components/TodoCreate'

export default {
  name: 'Home',
  components: {
    'todo-element': TodoElement,
    'todo-create': TodoCreate
  },
  data () {
    return {
      todos: []
    }
  },
  methods: {
    addTodo (todo) {
      this.$resource('todos{/id}').save(todo).then(res => this.todos.push(res.body))
    },
    updateTodo (todo) {
      this.$resource('todos{/id}').update({id: todo.id}, todo).then(res => {
        this.todos = this.todos.map(e => (e.id === res.body.id) ? res.body : e)
      })
    },
    deleteTodo (todo) {
      this.$resource('todos{/id}').delete({id: todo.id}).then(res => {
        const index = this.todos.findIndex(e => e.id === todo.id)
        this.todos = this.todos.slice(0, index).concat(this.todos.slice(index + 1))
      })
    }
  },
  created () {
    this.$resource('todos{/id}').get().then(res => {
      this.todos = res.body
    })
  }
}
</script>
