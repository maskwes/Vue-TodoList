<template>
  <div>
    <h2>List</h2>
    <router-link to="/">Home</router-link>
    <hr>
    <AddTodo @add-todo="addTodo"></AddTodo>
    <select v-model="filter">
      <option value="all">All</option>
      <option value="completed">completed</option>
      <option value="not-completed">not-completed</option>
    </select>
    <hr>
    <Loader v-if="loading"></Loader>
    <Todolist 
    v-else-if="filteredTodos.length"
        v-bind:todos="filteredTodos" 
        @remove-todo="removeTodo">
    </Todolist>
    <p v-else>No todos!</p>
  </div>
</template>

<script>
import Todolist from'@/components/Todo-list'
import AddTodo from'@/components/AddTodo'
import Loader from'@/components/Loader'

export default {
  name: 'App',
  data(){
    return{
      todos:[],
      loading:true,
      filter:'all'
    }
  },
  mounted() {
  fetch('https://jsonplaceholder.typicode.com/todos?_limit=3')
    .then(response => response.json())
    .then(json => {this.todos=json
    setTimeout(()=>{ 
      this.todos=json
      this.loading=false
      },1000)
    })
    
  },
  // watch:{
  //   filter(value){
  //     console.log(value)
  //   }
  // },
  computed:{
    filteredTodos(){
      if(this.filter==='all')
      {
        return this.todos
      }
      if(this.filter==='completed')
      {
        return this.todos.filter(t=>t.completed)
      }
      if(this.filter==='not-completed')
      {
        return this.todos.filter(t=>!t.completed)
      }
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
    AddTodo,
    Loader
  }
}
</script>