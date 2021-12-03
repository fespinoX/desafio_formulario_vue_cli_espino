<template>
    <v-data-table
        :headers="tablaheaders"
        :items="mockgatos"
        class="elevation-1"
        hide-default-footer
    >

    </v-data-table>
</template>

<script>

  // Data
  import mockgatos from "./../assets/data/mockgatos.json"
  import tablaheaders from "./../assets/data/tablaheaders.json"

  export default {
    name: 'TablaGatos',
    props: {
    },
    data: () => ({
      mockgatos,
      tablaheaders
    }),
  }

</script>