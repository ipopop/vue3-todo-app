<template>
  <h1>Veille techno</h1>
  <Form @add="saveTechno" />
  <br />
  <TechnoList :technos="technos" @delete-techno="deleteTechno" />
</template>

<script>
import Form from "@/components/Form"
import TechnoList from "@/components/TechnoList"
import { ref } from 'vue'
export default {
  name: 'App',
  components: {
    Form,
    TechnoList
  },
  setup() {
    let technos = ref([])

    const saveTechno = function (data) {
      console.log("App | saveTechno | data : ", data)
      technos.value = [...technos.value, { techno: data, id: Date.now() }]
      console.log("App | saveTechno | technos.value : ", technos.value)
    }

    const deleteTechno = function(tech) {
      console.log("App | deleteTechno() | tech", tech);
    }
    
    return {
      saveTechno,
      deleteTechno,
      technos
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
}

ul {
  list-style: none;
}
</style>
