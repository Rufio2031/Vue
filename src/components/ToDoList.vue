<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done == true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done == false}).length}}</p>
    
    <!--Todo Component-->
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="(todo, index) in todos" v-bind:todo.sync="todo"></todo>
  </div>
</template>

<script>
    import Todo from './Todo'

    export default {
      props: ['todos'],
      components: {
        Todo
      },
      methods: {
        deleteTodo (todo) {
          const todoIndex = this.todos.indexOf(todo)
          this.todos.splice(todoIndex, 1)
        },
        completeTodo (todo) {
          const todoIndex = this.todos.indexOf(todo)
          this.todos[todoIndex].done = true
        }
      }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped="">
  
</style>
