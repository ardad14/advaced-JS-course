<template>
  <ul v-if="this.listOfBreeds.length > 0">
    <li v-for="(breed, index) in this.listOfBreeds"
        :key="index">
      {{ breed }}
    </li>
  </ul>
  <div class="button-random">
    <button
        @click=this.addRandomBreed
    >
      Добавить породу
    </button>
    <button
        @click=this.deleteRandomBreed
    >
      Удалить породу
    </button>
    <button
        @click=this.shuffleBreeds
    >
      Перемешать список
    </button>
  </div>

</template>

<script>
import axios from "axios";

export default {
  name: "ListOfBreeds",
  data() {
    return {
      listOfBreeds: []
    }
  },
  methods: {
    addRandomBreed: function () {
      axios
          .get('https://dog.ceo/api/breeds/image/random')
          .then(response => {
            let imageLink = response.data.message;
            imageLink = imageLink.split('/');
            this.listOfBreeds.push(imageLink[imageLink.length - 2]);
          })
          .catch(error => {
            console.log(error);
          })
    },
    deleteRandomBreed: function () {
      let randomIndex = Math.floor(Math.random() * this.listOfBreeds.length)
      this.listOfBreeds.splice(randomIndex, 1);
    },
    shuffleBreeds: function () {
      this.listOfBreeds.sort(() => Math.random() - 0.5)
    }
  }
}
</script>

<style scoped>
.button-random {
  margin-left: 380px;
  font-family: 'Montserrat', sans-serif;
}

button {
  width: 200px;
  border-radius: 20px;
  padding: 10px;
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  margin-left: 20px;
  margin-bottom: 30px;
}
ul{
  margin-left: 650px;
  font-family: 'Montserrat', sans-serif;
  color: red;
  font-size: 22px;
}
li{
  padding-bottom: 10px;
}
</style>