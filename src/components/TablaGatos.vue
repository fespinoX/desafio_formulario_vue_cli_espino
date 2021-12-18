<template>
  <div
    class="mt-6"
  >
    <h2
      class="mb-6 text-center"
    >
      Estos son todos los michis (por ahora...)
    </h2>

    <v-data-table
      :headers="tablaheaders"
      :items="michis"
      class="elevation-1 mt-2"
      :loading="loadingMichis"
    >
      <template
        v-slot:body="{ items }"
      >
        <tbody>
          <tr
            v-for="item in items"
            :key="item.id"
          >
            <td class="text-left">{{ item.nombre }}</td>
            <td class="text-left">{{ item.humano }}</td>
            <td class="text-left">
              {{ item.edad }}
              <span
                v-if="item.edad === '1'"
              >
                año
              </span>
              <span
                v-else
              >
                años
              </span>
            </td>
            <td class="text-left">{{ item.color }}</td>
            <td class="text-left">
              <v-icon
                small
                v-if="item.panza"
              >
                mdi-check
              </v-icon>
              <v-icon
                small
                v-else
              >
                mdi-close-circle-outline
              </v-icon>
            </td>
          </tr>
        </tbody>
      </template>
    </v-data-table>

  </div>
</template>

<script>

  import { mapState } from "vuex"
  
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
      tablaheaders,
    }),

    computed : {
      ...mapState({
        michis: state => state.michis,
        loadingMichis: state => state.loadingMichis,
      }),

    },

    watch : {
      
    }
    
    
  }

</script>