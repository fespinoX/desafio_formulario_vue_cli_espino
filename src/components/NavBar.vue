<template>
  <v-app-bar
    app
    color="primary"
    dark
  >
    <v-spacer></v-spacer>
    <router-link to="/">
      <div
        class="mr-4"
      >
        <v-icon>mdi-plus-box-multiple</v-icon>
        <span>Agregar michi</span>
      </div>
    </router-link>  
      <router-link to="/michis">
        <div
          class="mr-4"
        >      
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
    color: white!important
    text-decoration: none

  .user-card
    padding: 10px 20px

</style>
