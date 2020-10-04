<template>
    <h4>Toutes les technos à suivre</h4>
    <span class="nb">{{technos.length}} techno{{technos.length > 1 ? 's' : '' }}</span>
    <ul>
    <li v-for="tech in technos" :key="tech.id">
        <div><button @click="editTechno(tech)">edit</button></div>
        <span> {{tech.techno}}</span>
        <div><button @click="deleteTechno(tech)">x</button></div>
    </li>
    </ul>
</template>

<script>
export default {
    emits: ["delete-techno"],
    props: {
        technos: {
            type: Array,
            required: true
        }
    },
    setup(props, {emit}) {
        let deleteTechno = function(tech) {
            emit('delete-techno', tech)
        }
        return {
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
        display: flex;
        justify-content: space-between;
        margin: 10px 0;
    }

    span {
        width: 85%;
        margin: 0 20px;
        overflow: hidden;
        margin-top: 1px;
    }

    button {
        border: none;
        border-radius: 3px;
        padding: 0 auto;
        padding-bottom: 1px;
        margin-bottom: 3px;
        background-color: darkgray;
        list-style: none;
        list-style-type: none;
        list-style-position: outside;
        list-style-image: none;
    }
</style>