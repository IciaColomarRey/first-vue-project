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
                  v-model="productName"
                ></v-text-field>
                <v-textarea
                  name="input-7-1"
                  label="Descripción del producto"
                  v-model="productDesc"
                ></v-textarea>
                <v-text-field
                  label="Introduce URL imagen"
                  v-model="productImage"
                ></v-text-field>
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
            @click="saveData"
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
    dialog: false,
    productId: -1,
    productName: '',
    productDesc: '',
    productImage: '',
    editingCard: false // variable auxiliar que indica si la tarjeta mostrada existe o no
  }),
  props: [
    'dataCard'
  ],
  methods: {
    showModal (dataEditCard) {
      this.dialog = true
      if (typeof dataEditCard !== 'undefined') {
        this.productName = dataEditCard.title
        this.productDesc = dataEditCard.description
        this.productId = dataEditCard.id
        this.productImage = dataEditCard.imageSrc
        this.editingCard = true
      } else {
        this.editingCard = false
      }
    },
    saveData () {
      if (this.productName !== '' && this.productDesc !== '') {
        let newCard = { id: this.productId, title: this.productName, description: this.productDesc, imageSrc: this.productImage }
        this.dialog = false
        this.productName = ''
        this.productDesc = ''
        this.productImage = ''
        if (this.editingCard) {
          this.$emit('edit-card', newCard)
        } else {
          this.$emit('add-new-card', newCard)
        }
      }
    }
  }
}
</script>
