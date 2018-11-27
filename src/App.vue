<template>
  <div id="app">
    <Header v-on:open-modal="openModal" />
    <ModalForm ref="modalForm" v-on:add-new-card="addNewCard" v-on:edit-card="updateCardData" />
    <v-layout class="flex">
      <v-flex v-for="card in cardsArr" v-bind:key="card.id" >
        <StoreCard v-bind:card="card" v-on:delete-card="deleteCard" v-on:edit-card="openEditModal" />
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
      cardsArr: []
    }
  },
  methods: {
    openModal () {
      this.$refs.modalForm.showModal()
    },
    addNewCard (newCardData) {
      newCardData.id = this.cardsArr.length
      this.cardsArr.push(newCardData)
      this.saveData()
    },
    updateCardData (newCardData) {
      let cardToUpdate = this.cardsArr.find(card => card.id === newCardData.id)
      cardToUpdate.title = newCardData.title
      cardToUpdate.description = newCardData.description
      cardToUpdate.imageSrc = newCardData.imageSrc
      this.saveData()
    },
    deleteCard (idCard) {
      const deleteCard = this.cardsArr.find(card => card.id === idCard)
      var pos = this.cardsArr.indexOf(deleteCard)
      this.cardsArr.splice(pos, 1)
      this.saveData()
    },
    openEditModal (cardToEdit) {
      const dataEditCard = this.cardsArr.find(card => card === cardToEdit)
      this.$refs.modalForm.showModal(dataEditCard)
    },
    saveData () {
      localStorage.setItem('cardsArray', JSON.stringify(this.cardsArr))
    }
  },
  mounted () {
    // cargamos los datos desde local Storage
    let dataLC = JSON.parse(localStorage.getItem('cardsArray'))

    if (dataLC !== null) {
      this.cardsArr = dataLC
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
.flex {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  align-items: center;
}
</style>
