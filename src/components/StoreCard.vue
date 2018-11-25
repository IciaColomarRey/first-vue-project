<template>
  <v-layout class="card">
    <v-flex xs12 sm6 offset-sm3>
      <v-card >
        <v-img
          src="https://cdn.vuetifyjs.com/images/cards/desert.jpg"
          aspect-ratio="2.25"
        ></v-img>
        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">{{ card.title }}</h3>
            <p>{{ card.description }}</p>
          </div>
        </v-card-title>
        <v-card-actions>
          <v-btn flat color="green">Editar</v-btn>
          <v-btn flat color="red">Borrar</v-btn>
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
  }
}
</script>

<style scoped>
.card {
  margin: 30px;
}
</style>
