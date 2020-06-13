<template>
    <li>
          <v-card
    class="mx-auto"
    max-width="500"
  >
    <v-card-text>
      <p class="display-1 text--primary" v-bind:class="{done: todo.completed}">
       {{index+1+"."+todo.title | uppercase}}
      </p>
      <p>adjective</p>
      <div class="text--primary">
     {{todo.text}}
      </div>
    </v-card-text>
    <v-card-actions>
      <v-btn v-on:click="todo.completed=!todo.completed"
        text
        color="deep-purple accent-4"
      >
        Complited
      </v-btn>
        <v-btn v-on:click="$emit('remove-todo',todo.id)"
        text
        color="deep-purple accent-4"
      >
        Delete
      </v-btn>
    </v-card-actions>
  </v-card> 
    </li>
</template>

<script>
export default {
    props:{
        todo:{
            type: Object,
            required:true
        },
        index:Number
    },
    filters:{
        uppercase(value){
            console.log(value)
            return value.toUpperCase()
        }
    }

}
</script>

<style >
    li{
        padding-bottom: 20px;
    }
    .done{
        text-decoration: line-through;
    }
    input{
        margin-right: 1rem;
    }
</style> 