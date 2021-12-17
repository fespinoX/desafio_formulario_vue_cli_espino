<template>
  <div>

    <v-data-table
      :headers="tablaheaders"
      :items="michis"
      class="elevation-1"
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
                v-if="item.edad === 1"
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
  import axios from "axios"

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
      michis: []
    }),

    methods: {

      levantarMichis() {
        console.log("levantndo michis....")
        axios
          .get('https://61b145c33c954f001722a877.mockapi.io/michis')
          .then(response => (this.info = response))
          .then(data => {
            this.michis = data.data
            console.log("michis levantados de la DB")
          })
          .catch((err) => {console.error(`${err}`)})
      },

    },

    mounted() {
      console.log("buenas buenas")
      this.$nextTick(function () {
        this.levantarMichis()
      })

    }  
    
    
  }

</script>