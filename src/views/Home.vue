<template>
  <div>
    <NavBar />
    <v-container>
      <v-row class="text-center">
        <v-col cols="12">
          <v-img
            :src="require('../assets/cator.png')"
            class="my-3"
            contain
            height="120"
          />
        </v-col>

        <v-col
          cols="12"
          class="mb-4"
        >
          <h1 class="display-2 font-weight-bold mb-3">
            {{ nombreApp | mayusculizar(nombreApp) }}
          </h1>

          <p class="subheading font-weight-regular">
            Agreguemos michis porque si:
          </p>
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">
          <AgregarGatoForm @click="submit" />
        </v-col>
      </v-row>

    </v-container>
  </div>
</template>

<script>

  // Components
  import NavBar from './../components/NavBar.vue';
  import AgregarGatoForm from './../components/AgregarGatoForm.vue';
  
  // Data
  import mockgatos from "./../assets/data/mockgatos.json"

  export default {
    name: 'Home',
    components: {
      NavBar,
      AgregarGatoForm,
    },
    filters: {
      mayusculizar: (value) => {
        if (!value) return ''
        value = value.toString()
        return value.toUpperCase()
      },
    },
    data: () => ({
      mockgatos,
      nombreApp: 'vuecator 2000'
    }),
    methods : {
      submit(michiagregado) {
        let listaGatos = this.mockgatos
        listaGatos.push(michiagregado)
        this.mockgatos = listaGatos
      }
    }
  }
</script>
