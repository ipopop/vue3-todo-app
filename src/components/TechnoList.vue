<template>
    <h4>Toutes les technos à suivre</h4>
    <span class="nb">{{technos.length}} techno{{technos.length > 1 ? 's' : '' }}</span>
    <ul>
    <li v-for="tech in technos" :key="tech.id">
        <div v-if="technoToEdit !== null && technoToEdit.id === tech.id">
            <div>
                <button @click="save">save</button>
                <span>
                    <input type="text" v-model="technoToEdit.techno" @keypress.enter="save" />
                </span>
            </div>
        </div>
        <div v-else>
            <div>
                <button @click="editTechno(tech)">edit</button>
                <span>
                    {{tech.techno}}
                </span>
            </div>
        </div>
        <div>
            <button @click="deleteTechno(tech)">x</button>
        </div>
    </li>
    </ul>
</template>

<script>
import { ref } from 'vue'
export default {
    emits: ["edit-techno", "delete-techno"],
    props: {
        technos: {
            type: Array,
            required: true
        }
    },
    setup(props, { emit }) {
        let technoToEdit = ref(null)

        let editTechno = function(tech) {
            technoToEdit.value = tech
        }

        let deleteTechno = function(tech) {
            emit('delete-techno', tech)
        }

        let save = function() {
            emit("edit-techno", technoToEdit.value)
            technoToEdit.value = null
        }

        return {
            editTechno,
            technoToEdit,
            save,
            deleteTechno
        }
    }
}
</script>

<style>
    h4 {
        color: gainsboro;
    }

    .nb {
        color: gray;
    }

    ul {
        list-style: none;
        padding-left: 0px;
        text-align: left;
    }

    li {
        height: 32px;
        margin: 10px 0;
        display: flex;
        justify-content: space-between;
    }

    input {
        border: none;
        height: 25px;
        max-width: 150px;
        border-radius: 3px;
        font-family: Avenir, Helvetica, Arial, sans-serif;
        font-size: 17px;
    }

    span {
        width: 85%;
        margin: 0 20px;
        margin-top: 1px;
        overflow: hidden;
    }

    button {
        border: none;
        list-style: none;
        list-style-type: none;
        list-style-position: outside;
        list-style-image: none;
        height: 21px;
        border-radius: 3px;
        padding-bottom: 1px;
        margin-bottom: 3px;
        background-color: darkgray;
    }
</style>