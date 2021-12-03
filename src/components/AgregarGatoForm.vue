<template>
  <div>
    <h1 class="page-guia">Registro</h1>    

    <v-form v-model="valid">
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
            value=true
            hide-details
            :rules="checkRules"
          ></v-checkbox>
          <v-checkbox
            v-model="panza"
            label="No"
            color="orange darken-3"
            value=false
            :rules="checkRules"
          ></v-checkbox>
        </v-col>

        <v-col
          cols="12"
          md="6"
          offset-md="3"
        >
          <v-btn
            class="form-submit mt-4"
            @click="submit"
            color="orange"
          >
            submit
          </v-btn>
        </v-col>

      </v-row>
    </v-container>
  </v-form>
  </div>
</template>

<script>
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
      nuevoMichi: '',
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
        v => ( v && v >= 0 ) || 'La edad no uede ser menor de 0',
      ],
      checkRules: [
        v => !!v || 'Por favor seleccione una opción',
      ]
    }),
    methods: {
      submit() {
        if (this.valid) {
          // this.nuevoMichi
          console.log("agregado el michi: " + this.nuevoMichi)
          this.$emit('click', this.nuevoMichi);
        }
      }
    }
  }
</script>
