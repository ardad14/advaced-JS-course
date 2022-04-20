<template>
    <BreedComponent
        v-for="(breed, key) in this.allBreeds"
        :key="breed.id"
        :name="key"
        :subbreeds="breed"
    />
</template>

<script>
import axios from "axios";
import BreedComponent from "@/components/BreedComponent";

export default {
    name: "GreetingTask",
    components: {
        BreedComponent,
    },

    data() {
        return {
            userName: 'незнакомец',
            inputText: '',
            allBreeds: [],
            randomBreed: []
        }
    },
    mounted() {
        axios
            .get('https://dog.ceo/api/breeds/list/all')
            .then(response => {
                this.allBreeds = response.data.message;
            })
            .catch(error => {
                console.log(error);
            })
    },
    watch: {
        inputText() {
            this.userName = this.inputText;
            if (this.inputText === '') {
                this.userName = 'незнакомец';
            }
        }
    }
}
</script>

<style scoped>

</style>
