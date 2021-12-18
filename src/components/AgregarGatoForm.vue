<template>
  <div>
    <h2
      class="mb-4 text-center"
    >
      Agreguemos un michi
    </h2>
    <v-form
      ref="form"
      v-model="valid"
      lazy-validation
    >
    <v-container>
      <v-row>
        <v-col
          cols="12"
          md="6"
          offset-md="3"
        >
          <v-text-field
            v-model="nombre"
            :rules="textRules"
            :counter="10"
            label="Nombre del michi"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="6"
          offset-md="3"
        >
          <v-select
            :items="listahumanos"
            label="Humano del michi"
            v-model="humano"
            :rules="textRules"
          ></v-select>
        </v-col>

        <v-col
          cols="12"
          md="6"
          offset-md="3"
        >
          <v-text-field
            v-model="edad"
            :rules="edadRules"
            single-line
            type="number"
            label="Edad del michi"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="6"
          offset-md="3"
        >
          <v-text-field
            v-model="color"
            :rules="textRules"
            :counter="10"
            label="Color del michi"
            required
          ></v-text-field>
        </v-col>

        <v-col
          cols="12"
          md="6"
          offset-md="3"
        >
          <p>Se deja rascar la panza?</p>
          <v-checkbox
            v-model="panza"
            label="Sí"
            color="orange"
            value="Sí"
            hide-details
            :rules="checkRules"
          ></v-checkbox>
          <v-checkbox
            v-model="panza"
            label="No"
            color="orange darken-3"
            value="No"
            :rules="checkRules"
          ></v-checkbox>
        </v-col>

        <v-col
          cols="12"
          md="6"
          offset-md="3"
          class="text-center"
        >
          <v-btn
            class="form-submit mt-4"
            @click="submit"
            color="orange"
          >
            submit
          </v-btn>

        </v-col>

        <v-col
          cols="12"
        >
          <v-alert
            :value="alert"
            color="green"
            dark
            type="success"
            transition="scale-transition"
          >
            Agregaste un michi!
          </v-alert>
        </v-col>

      </v-row>
    </v-container>
  </v-form>
  </div>
</template>

<script>
  // import axios from "axios"
  // import vuex from "vuex"

  export default {
    name: 'AgregarGatoForm',

    data: () => ({
      listahumanos: [
        'Fespi',
        'Amanda',
        'Leo',
        'Flor',
        'Otro'
      ],
      
      valid: false,

      nuevoMichi: {},
      nombre: '',
      humano: '',
      edad: '',
      color: '',
      panza: false,

      textRules: [
        v => !!v || 'Por favor complete este campo',
        v => v.length >= 3 || 'Este campo debe contener al menos 3 caracteres',
      ],
      requiredRules: [
        v => !!v || 'Por favor complete este campo',
      ],
      edadRules: [
        v => !!v || 'Por favor complete este campo.',
        v => ( v && v >= 0 ) || 'La edad no puede ser menor a 0',
        v => ( v && v <= 30 ) || 'La edad no puede ser mayor a 30',
      ],
      checkRules: [
        v => !!v || 'Por favor seleccione una opción',
      ],

      alert: false,
    }),
    methods: {
      submit() {
        if (this.$refs.form.validate()) {
          // agrega la data del form a nuevoMichi
          this.nuevoMichi.nombre = this.nombre
          this.nuevoMichi.humano = this.humano
          this.nuevoMichi.edad = this.edad
          this.nuevoMichi.color = this.color
          this.nuevoMichi.panza = this.panza


          // agrega el nuevo michi
          this.agregarMichiNuevo(this.nuevoMichi)

          // muestra la alerta
          this.showAlert()

          // vacía formulario
          this.vaciarForm()
          
          // resettea la validacion
          this.$refs.form.resetValidation()
        } else {
          console.log("no valida")
        }
      },

      agregarMichiNuevo(michinuevo) {

        this.$store.dispatch("agregarMichi", michinuevo)

        console.log("michi nuevo aca es:", michinuevo)

      },

      showAlert() {
        this.alert = false
        this.alert = true
        setTimeout(() => {
          this.alert=false
        },5000)
      },

      vaciarForm() {
        this.nombre = ''
        this.humano = ''
        this.edad = ''
        this.color = ''
        this.panza = ''
      },

    }
  }
</script>
