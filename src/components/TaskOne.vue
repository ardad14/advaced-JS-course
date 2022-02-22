<template>
  <!-- Task1, 2  -->
  <div class="task1">
    <div class="hello_task">
      <h5>Привет, <strong>{{ userName }}</strong></h5>
      <input v-model="inputText" type="text">
    </div>
    <!-- Task3  -->
    <h2>Породы собак</h2></div>
</template>

<script>
export default {
  name: "TaskOne",
  data() {
    return {
      userName: 'незнакомец',
      inputText: '',
    }
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
.task1 {
  margin-left: 600px;
  font-family: 'Montserrat', sans-serif;
}

h5 strong {
  color: red;
}

.task1 h5 {
  font-size: 20px;
  font-family: 'Montserrat', sans-serif;
  margin-left: -150px;
}

.task1 input {
  width: 300px;
  position: relative;
  bottom: -25px;
  height: 25px;
  font-size: 14px;
  border-radius: 30px;
  margin-left: 70px;
  padding: 5px;
  font-family: 'Montserrat', sans-serif;

}

.hello_task {
  display: flex;
  font-family: 'Montserrat', sans-serif;

}

.task1 h2 {
  font-family: 'Montserrat', sans-serif;
  margin-left: 80px;
  font-size: 30px;
  font-weight: 500;
}
</style>