<template>
  <div id="app">
    <h1>ЫФВЫ</h1>
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
      todos:[
        {id:1,title:'asdasdasdas',completed:false},
        {id:2,title:'жмых',completed:false},
        {id:3,title:'dddd',completed:false}
      ]
    }
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
