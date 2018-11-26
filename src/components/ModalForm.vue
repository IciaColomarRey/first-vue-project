<template>
  <div class="text-xs-center">
    <v-dialog v-model="dialog" width="500" >
      <v-card>
        <v-card-title
          class="headline grey lighten-2"
          primary-title
        >
          Formulario de producto
        </v-card-title>

        <v-card-text>
          <v-form>
            <v-container>
              <v-layout column>
                <v-text-field
                  label="Nombre del producto"
                  :counter="30"
                ></v-text-field>
                <v-textarea
                  name="input-7-1"
                  label="Descripción del producto"
                  value=""
                ></v-textarea>
              </v-layout>
            </v-container>
          </v-form>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="green"
            flat
            @click="dialog = false"
          >
            Guardar
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data: () => ({
    dialog: false
  }),
  methods: {
    showModal () {
      this.dialog = true
    }
  }
}
</script>
