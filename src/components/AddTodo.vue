<template>
    <form @submit.prevent="onSubmit">
    <div>
        <v-text-field label="Enter the task" :rules="rules" hide-details="auto" v-model="title"></v-text-field>
        <v-text-field label="Another input" v-model="text"></v-text-field>
    </div>
    <v-btn type="submit" large color="primary">Primary</v-btn>    
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