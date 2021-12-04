<template>
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

      <v-col class="mb-4">
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
    <v-row>
      <v-col cols="12" class="mb-6">
        <h2 class="mb-2 text-center">Los michis</h2>
        <TablaGatos :content="mockgatos" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>

  // Components
  import AgregarGatoForm from './AgregarGatoForm';
  import TablaGatos from './TablaGatos';

  // Data
  import mockgatos from "./../assets/data/mockgatos.json"

  export default {
    name: 'MainPage',
    components: {
      AgregarGatoForm,
      TablaGatos,
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
