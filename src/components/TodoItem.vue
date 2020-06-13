<template>
    <li>
        <md-card class="md-accent" md-with-hover>
        <md-ripple>
            <md-card-header>
            <div class="md-title" v-bind:class="{done: todo.completed}">{{index+1+"."+todo.title | uppercase}}</div>
            </md-card-header>  
            <md-card-content>
                {{todo.text}}
            </md-card-content>
            <md-card-actions>
            <md-button  name="" id="" v-on:click="todo.completed=!todo.completed">Complited</md-button>
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