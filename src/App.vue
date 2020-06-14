<template>
  <v-app>
    <AppHeader></AppHeader>
    <div id="app" class="wrapper">

    <hr>
    <router-view/>
  </div>
  </v-app>
</template>

<script>
import AppHeader from'@/components/AppHeader'

export default {
  name: 'App',

  data: () => ({
    //
  }),
  components:{
    AppHeader

  }
};
</script>

