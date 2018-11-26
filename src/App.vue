<template>
  <div id="app">
    <Header v-on:open-modal="openModal" />
    <ModalForm ref="modalForm" />
    <v-layout justify-center>
      <v-flex xs12 sm6 v-for="card in cardsArr" v-bind:key="card.id">
        <StoreCard v-bind:card="card"/>
      </v-flex>
    </v-layout>
    <Footer />
  </div>
</template>

<script>
import Header from './components/Header'
import ModalForm from './components/ModalForm'
import StoreCard from './components/StoreCard'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    ModalForm,
    StoreCard,
    Footer
  },
  data () {
    return {
      cardsArr: [
        { id: 0, title: 'titulo1', description: 'Descripción 1', imageSrc: 'cadena' },
        { id: 1, title: 'titulo2', description: 'Descripción 2', imageSrc: 'cadena' },
        { id: 2, title: 'titulo3', description: 'Descripción 3', imageSrc: 'cadena' }
      ]
    }
  },
  methods: {
    openModal () {
      this.$refs.modalForm.showModal()
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
