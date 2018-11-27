<template>
  <v-layout >
    <v-flex class="card">
      <v-card>
        <v-img
          v-bind:src="card.imageSrc"
          aspect-ratio="2.25"
        ></v-img>
        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">{{ card.title }}</h3>
            <p>{{ card.description }}</p>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat color="green" @click="editCard">Editar</v-btn>
          <v-btn flat color="red" @click="deleteCard">Borrar</v-btn>
        </v-card-actions>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  name: 'StoreCard',
  props: [
    'card'
  ],
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {
    deleteCard () {
      this.$emit('delete-card', this.card.id)
    },
    editCard () {
      this.$emit('edit-card', this.card)
    }
  }
}
</script>

<style scoped>
.card {
  margin: 30px;
}
</style>
