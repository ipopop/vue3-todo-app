<template>
    <h3>Toutes les technos à surveiller</h3>
    {{technos.length}} techno{{technos.length > 1 ? 's' : '' }}
    <ul>
    <li class="flex-column" v-for="tech in technos" :key="tech.id"><button @click="deleteTechno(tech)">x</button> {{tech.techno}}</li>
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


</style>