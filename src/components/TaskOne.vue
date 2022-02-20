<template>
  <!-- Task1, 2  -->
  <div class="task1">
    <h1 class="h1">Приветственное поле</h1>
    <div class="hello_task">
      <h5>Привет, {{ userName }}</h5>
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

.task1 h5 {
  font-size: 20px;
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
}

.hello_task {
  display: flex;
}

.task1 h2 {
  margin-left: 80px;
  font-size: 24px;
}
</style>