<template>
  <div class="michis">
    <NavBar />
    <h2 class="mb-2 text-center">Estos son todos los michis</h2>
    <TablaGatos />
  </div>
</template>

<script>
// Components
import NavBar from './../components/NavBar.vue';
import  TablaGatos from './../components/TablaGatos.vue'

// Data

export default {
  name: 'Michis',
  components: {
    NavBar,
    TablaGatos,
  },
  data: () => ({
  }),
}
</script>
