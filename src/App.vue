<template>
  <h1>Veille techno</h1>
  <Form @add="saveTechno" />
  <br />
  <TechnoList :technos="technos" @delete-techno="deleteTechno" @edit-techno="editTechno" />
  <br />
  <footer><p>Todolist with Vue.js 3</p></footer>
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

    const editTechno = function(tech) {
      technos.value = technos.value.map(t => t.id !== tech.id ? t : tech)
    }

    const deleteTechno = function(tech) {
      console.log("App | deleteTechno() | tech", tech);
      technos.value = technos.value.filter(t => t.id !== tech.id)
    }
    
    return {
      technos,
      saveTechno,
      editTechno,
      deleteTechno,
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
  width: 90%;
  max-width: 333px;
  margin: 0 auto;
  margin-top: 60px;
}
footer p {
  margin-top: 50px;
  font-size: 0.75rem;
  color: dimgrey;
}
</style>
