<template>
<!-- Task1, 2  -->
    <h1 class="h1">Приветсвтвеное поле</h1>
    <h5>Привет, {{userName}}</h5>
    <input v-model="inputText" type="text">
<!-- Task3  -->
<h1>Породы собак</h1>
    <BreedComponent
        v-for="(breed, key) in this.allBreeds"
        :key="breed.id"
        :name="key"
        :subbreeds="breed"
    />
<!-- Task4 -->
<h1>Случайная порода собаки</h1>
    <RandomBreed />
<!-- Task5 -->
    <h1>Список пород</h1>
    <ListOfBreeds />

</template>

<script>
import axios from "axios";
import BreedComponent from "@/components/BreedComponent";
import RandomBreed from "@/components/RandomBreed";
import ListOfBreeds from "@/components/ListOfBreeds";

export default {
    name: "GreetingTask",
    components: {
        BreedComponent,
        RandomBreed,
        ListOfBreeds
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