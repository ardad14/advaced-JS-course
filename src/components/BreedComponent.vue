<template class="block_row">
  <div class="block_row">
    <div class="elements">
      <h4>Порода: {{ name }}</h4>
      <img :src=this.image alt="">
      <ul v-if="subbreeds.length > 0">
          <li v-for="breed in subbreeds"
              :key="breed.id">
            {{ breed }}
          </li>
      </ul>
    </div>
  </div>
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
  display: flex;
}

img {
  width: 225px;
  height: 200px;
}

h4 {
  margin-left: 70px;
}

.elements {
  border: 2px solid red;
  width: 300px;
  border-radius: 20px;
  height: 750px;
  background-color: #f5efef;
}

.block_row {
  margin-bottom: 20px;
  margin-left: 60px;
}

</style>