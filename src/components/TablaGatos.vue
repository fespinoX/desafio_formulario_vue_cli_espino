<template>
    <v-data-table
        :headers="tablaheaders"
        class="elevation-1"
        hide-default-footer
        :items="content"
    >

    </v-data-table>
</template>

<script>

  // Data
  import tablaheaders from "./../assets/data/tablaheaders.json"

  export default {
    name: 'TablaGatos',
    props: {
      content: {
        type: Array
      }
    },
    data: () => ({
      tablaheaders
    }),
  }

</script>