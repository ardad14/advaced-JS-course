<template>
    <h4>Порода: {{name}}</h4>
    <img :src=this.image alt="">
    <ul v-if="subbreeds.length > 0">
        <li v-for="breed in subbreeds"
        :key="breed.id">
            {{breed}}
        </li>
    </ul>
</template>

<script>
import axios from "axios";

export default {
    name: "BreedComponent",
    props: {
        name: String,
        subbreeds: Array
    },
    data() {
        return {
            image: String
        }
    },
    mounted() {
        axios
            .get(`https://dog.ceo/api/breed/${this.name}/images/random`)
            .then(response => {
                this.image = response.data.message;
            })
            .catch(error => {
                console.log(error);
            })
    },
    methods: {
        ucFirst: function (string) {
            return string[0].toUpperCase() + string.substring(1)
        }
    }
}
</script>

<style scoped>
    li {
        color: red;
        font-weight: 700;
        font-style: italic;
    }
</style>