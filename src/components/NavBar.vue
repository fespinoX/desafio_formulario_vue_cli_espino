<template>
  <v-app-bar
    app
    color="primary"
    dark
  >
    <v-spacer></v-spacer>
    <router-link to="/">
      <div>
        <v-icon>mdi-plus-box-multiple</v-icon>
        <span>Agregar michi</span>
      </div>
    </router-link>  
      <router-link to="/michis">
        <div>      
          <v-icon>mdi-format-list-bulleted</v-icon>
          <span>Todos los michis</span>
        </div>
    </router-link>

  </v-app-bar>
</template>

<script>

export default {
  name: 'NavBar',

  components: {

  },

  props: {
  },

  data: () => ({
  }),

};

</script>

<style lang="sass" scoped>
  
  a
    display: inline-block
    color: white!important
    text-decoration: none

    span
      margin-left: 5px
    
    &:first-of-type
      margin-right: 20px

</style>
