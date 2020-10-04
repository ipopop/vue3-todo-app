/* eslint-disable vue/no-parsing-error */
<template>
    <form @submit.prevent="addTechno">
        <label for="techno">Techno a ajouter</label>
        <input class="addTechno" type="text" name="techno" v-model="techToLearn" />
        <button type="submit">ajouter</button>
    </form>
</template>

<script>
import { ref } from 'vue'
export default {
    setup(props, ctx) {
        let techToLearn = ref("") 

        const addTechno = function() {
            console.log("Form | addTechno() | techToLearn.value : ", techToLearn.value)
            ctx.emit("add", techToLearn.value)
            techToLearn.value = ""
        }

        return {
            techToLearn,
            addTechno
        }
    }
}
</script>

<style>
    form {
        width: fit-content;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
    }

    .addTechno {
        text-align: center;
    }

    label {
        margin-bottom: 20px;
    }

    button {
        width: fit-content;
        margin: 0 auto;
        margin-top: 16px;
    }
</style>