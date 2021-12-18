<template>
  <div>
    <NavBar />
    <v-container>
      <v-row class="text-center mt-6">
        <v-col cols="12 mt-6">
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
        </v-col>
      </v-row>

      <v-row>
        <v-col cols="12">
          <AgregarGatoForm />
        </v-col>
      </v-row>

    </v-container>
  </div>
</template>

<script>

  // Components
  import NavBar from './../components/NavBar.vue';
  import AgregarGatoForm from './../components/AgregarGatoForm.vue';

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
      nombreApp: 'vuecator 2000'
    }),
    methods : {
    },
    computed: {

    }
  }
</script>
