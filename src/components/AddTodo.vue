<template>
    <form @submit.prevent="onSubmit">
        
    <md-field>
      <label>Enter the task</label>
      <md-input v-model="title"></md-input>
    </md-field>
        <md-button type="submit" class="md-raised md-primary">Primary</md-button>
    </form>
    
</template>
<script>
export default {

    data()
    {
        return{
            title:''
        }
    },
    methods:{
        onSubmit(){
            if(this.title.trim()){
                const newTodo={
                    id:Date.now(),
                    title:this.title,
                    completed:false
                }
                this.$emit('add-todo',newTodo)
                this.title=''
            }
        }
    }
}
</script>
  export default {
    name: 'TextFields',
    data: () => ({
      initial: 'Initial Value',
      type: null,
      withLabel: null,
      inline: null,
      number: null,
      textarea: null,
      autogrow: null,
      disabled: null
    })
  }
<style scoped>
    form{
        display: flex;
    }
    input{
        width:400px;
    }
</style>