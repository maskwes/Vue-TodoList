<template>
<li>
    <md-card class="md-accent" md-with-hover>
    <md-ripple>
        <md-card-header>
          <div class="md-title" v-bind:class="{done: todo.completed}">{{todo.title | uppercase}}</div>
        </md-card-header>  
        <span  >
            <input type="checkbox" name="" id="" v-on:change="todo.completed=!todo.completed">
            <strong>{{index+1}}</strong>
        </span>
        <md-card-content>
          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Optio itaque ea, nostrum odio. Dolores, sed accusantium quasi non.
        </md-card-content>

        <md-card-actions>
          <md-button  name="" id="" v-on:click="todo.completed=!todo.completed">Comlited</md-button>
          <md-button v-on:click="$emit('remove-todo',todo.id)">Delete</md-button>
        </md-card-actions>
    </md-ripple>
    </md-card>



    


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
    .done{
        text-decoration: line-through;
    }
    input{
        margin-right: 1rem;
    }
</style> 