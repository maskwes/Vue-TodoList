<template>
  <div>
    <h2>List</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <AddTodo @add-todo="addTodo"></AddTodo>
    <hr>
    <Todolist v-bind:todos="todos" @remove-todo="removeTodo"></Todolist>
  </div>
</template>

<script>
import Todolist from'@/components/Todo-list'
import AddTodo from'@/components/AddTodo'

export default {
  name: 'App',
  data(){
    return{
      todos:[]
    }
  },
  mounted() {
  fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
    .then(response => response.json())
    .then(json => this.todos=json)
  },
  methods:{
    removeTodo(id){
      this.todos=this.todos.filter(t=>t.id !==id)
    },
    addTodo(todo){
      this.todos.push(todo)
    }
  },
  components: {
    Todolist,
    AddTodo
  }
}
</script>