<template>
  <div id="app">
    <Header />
    <v-layout justify-center>
      <v-flex xs12 sm6 v-for="(card) in cardsArr">
        <StoreCard v-bind:card="card"/>
      </v-flex>
    </v-layout>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header'
import StoreCard from './components/StoreCard'
import ModalForm from './components/ModalForm'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    StoreCard,
    ModalForm,
    Footer
  },
  data () {
    return {
      cardsArr: [
        { id: 0, title: 'titulo1', description: 'Descripción 1', imageSrc: 'cadena' },
        { id: 1, title: 'titulo2', description: 'Descripción 2', imageSrc: 'cadena' },
        { id: 2, title: 'titulo3', description: 'Descripción 3', imageSrc: 'cadena' },
      ]
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
