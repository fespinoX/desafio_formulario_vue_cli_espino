<template>
  <v-app>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view />
  </v-app>
</template>

<script>
  export default {
    
    mounted() {
      this.$store.dispatch("levantarMichis")
    }

  }
</script>

