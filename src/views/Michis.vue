<template>
  <div class="michis">
    <h2 class="mb-2 text-center">Los michis</h2>
    <TablaGatos :content="mockgatos" />
  </div>
</template>

<script>
// Components
import  TablaGatos from './../components/TablaGatos.vue'

// Data
  import mockgatos from "./../assets/data/mockgatos.json"

export default {
  name: 'Michis',
  components: {
    TablaGatos,
  },
  data: () => ({
    mockgatos,
  }),
}
</script>
