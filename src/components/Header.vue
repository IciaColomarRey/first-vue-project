<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <v-btn
        slot="activator"
        color="red lighten-2"
        dark
        @click="this.openModal"
      >
        Añadir producto
      </v-btn>
  </div>
</template>

<script>

export default {
  name: 'Header',
  data () {
    return {
      msg: 'Vue Project'
    }
  },
  methods: {
    openModal () {
      this.$emit('open-modal')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit  to this component only -->
<style scoped>
.hello {
  background-color: #42b983;
  color: azure;
  position: fixed;
  width: 100%;
  top: 0;
  display: flex;
  justify-content: space-around;
  align-items: center;
  margin-bottom: 50px;
}
</style>
