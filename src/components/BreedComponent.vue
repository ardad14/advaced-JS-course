<template class="block_row">
  <div class="block_row">
    <div class="elements">
      <h4> Порода:
        <strong v-if="subbreeds.length>0"> {{ name }}</strong>
        <i v-else> {{ name }} </i>
      </h4>
      <img :src=this.image alt="">
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
  display: block;
  float: left;
  width: 80px;
  margin-left: 20px;
  margin-bottom: 2px;
}

ul {
  margin: 0;
  margin-top: 10px;
  padding: 0;

}

img {
  max-width: 225px;
  min-width: 225px;
  width: 100%;
  height: 200px;
}

h4 {
  margin-left: 70px;
  font-style: italic;
}

h4 strong {
  font-style: italic;
  color: red;
}

.elements {
  border: 2px solid red;
  width: 330px;
  border-radius: 20px;
  height: 330px;
  background-color: #f3eeee;
}

.block_row {
  margin-bottom: 20px;
  margin-left: 35px;
}
</style>
