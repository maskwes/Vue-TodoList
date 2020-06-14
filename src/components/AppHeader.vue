<template>
  <div>
    <v-app-bar
      color="deep-purple accent-4"
      dense
      dark
    >
      <v-toolbar-title>Todo</v-toolbar-title>
      <v-spacer></v-spacer>
        <v-toolbar-items>
            <v-btn text v-for="(item,i) in menuItems"  :to="item.route">
               <v-icon left v-html="item.icon"></v-icon>
                {{item.title}}
            </v-btn>
        </v-toolbar-items>
    </v-app-bar>
  </div>
</template>
<script>
export default {
    computed:{
        menuItems(){
            return[
                {
                    icon:"visibility",
                    title:"Список дел",
                    route:"/Todos"
                },
                 {
                    icon:"extension",
                    title:"Карта событий",
                    route:"/Celendar"
                },
                {
                    icon:"account_circle",
                    title:"Профиль",
                    route:"/Profile"
                },
                {
                    icon:"exit_to_app",
                    title:"Выйти",
                    route:"/LogOut"
                },
                {
                    icon:"input",
                    title:"Войти",
                    route:"/Login"
                },
                {
                    icon:"lock_open",
                    title:"Зарегестрироваться",
                    route:"/SignUp"
                },
            ]
            
        }
    }
}
</script>

<style scoped>
a:not(.md-button):hover{
    text-decoration: underline;
}
</style>