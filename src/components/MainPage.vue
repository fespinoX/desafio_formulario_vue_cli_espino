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
          Vuecator 2000
        </h1>

        <p class="subheading font-weight-regular">
          explicar un poquito el proyecto
        </p>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <AgregarGatoForm @click="submit" />
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <p>tabla</p>
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
    data: () => ({
      mockgatos,
    }),
    methods : {
      submit(nuevomichi) {
        this.mockgatos.push(nuevomichi)
      }
    }
  }
</script>
