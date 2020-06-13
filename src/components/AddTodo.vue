<template>
    <form @submit.prevent="onSubmit">
        
    <md-field>
      <label>Enter the task</label>
      <md-input v-model="title"></md-input>
    </md-field>
         
    <md-field>
      <label>Enter the task</label>
      <md-textarea v-model="text"></md-textarea>
    </md-field>
        <md-button type="submit" class="md-raised md-primary">Primary</md-button>
    </form>
    
</template>
<script>
export default {
    data()
    {
        return{
            title:'',
            text:''
        }
    },
    methods:{
        onSubmit(){
            if(this.title.trim()){
                const newTodo={
                    id:Date.now(),
                    title:this.title,
                    text:this.text,
                    completed:false
                }
                this.$emit('add-todo',newTodo)
                this.title=''
                this.text=''
            }
        }
    }
}
</script>
<style scoped>
    form{
        display: flex;
    }
    .md-input{
        width:400px;
        border: 1px solid black;
        border-radius: 5px;
        padding: 5px;
    }
    label{
        padding-left: 5px;
    }
    .md-field + .md-has-textarea:not(.md-autogrow){
        margin-top: 20px;
           border: 1px solid black;
        border-radius: 5px;
    }
</style>