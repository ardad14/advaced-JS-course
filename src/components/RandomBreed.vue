<template>
  <div class="random">
    <h4 :hidden=!this.visibility><strong>Порода:</strong> {{ name }}</h4>
    <ul v-if="this.subBreed.length > 0">
      <li v-for="breed in this.subBreed"
          :key="breed.id">
        {{ breed }}
      </li>
    </ul>
    <img :src=image alt=""  :hidden=!this.visibility>
    <button
        @click=this.getRandomBreed
    >
      Получить породу
    </button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "RandomBreed",
  data() {
    return {
      randomBreed: [],
      subBreed: [],
      image: '',
      name: '',
      visibility: false
    }
  },
  methods: {
    getRandomBreed: function () {
      this.visibility = true
      axios
          .get('https://dog.ceo/api/breeds/image/random')
          .then(response => {
            this.randomBreed = response.data.message;
            this.image = this.randomBreed;
            this.name = this.randomBreed.split('/');
            this.name = this.name[this.name.length - 2];
          })
          .catch(error => {
            console.log(error);
          })
      axios
          .get(`https://dog.ceo/api/breed/${this.name}/list`)
          .then(response => {
            this.subBreed = response.data.message;
          })
          .catch(error => {
            console.log(error);
          })
    }
  }
}
</script>

<style scoped>
button {
  height: 45px;
  width: 100px;
  margin-top: -180px;

}

li {
  color: red;
  font-weight: 700;
  font-style: italic;
}

.random {
  display: flex;
}

img {
  width: 300px;
}

.random button {
  margin-left: 20px;
  width: 200px;
  border-radius: 20px;
  position: relative;
  font-family: 'Montserrat', sans-serif;
  font-size: 16px;
  bottom: -180px;
}

h4 {
  font-family: 'Montserrat', sans-serif;
  font-style: italic;
}

h4 strong {
  font-family: 'Montserrat', sans-serif;
  color: red;
}

</style>