<template>
  <div class="hello">
    <TaskOne></TaskOne>
  </div>
  <div class="animal">
    <GreetingTask></GreetingTask>
  </div>
  <hr>
  <div class="random-animal">
    <RandomBreed></RandomBreed>
  </div>
  <hr>
  <div class="add-animal-type">
    <h1>Список пород</h1>
    <ListOfBreeds></ListOfBreeds>
  </div>
</template>

<script>

import GreetingTask from "@/components/LabTasks";
import TaskOne from "@/components/TaskOne";
import RandomBreed from "@/components/RandomBreed";
import ListOfBreeds from "@/components/ListOfBreeds";
export default {
  name: 'App',
  components: {RandomBreed, TaskOne, GreetingTask,ListOfBreeds},
}
</script>

<style>

  .animal{
    display: flex;
    flex-wrap: wrap;
    width: 100%;
    font-family: 'Montserrat', sans-serif;
  }
  img{
    width: 30px;
    height: 250px;
    padding-left: 50px;
  }
  hr{
    margin-top: 50px;
  }
  .add-animal-type h1{
    font-family: 'Montserrat', sans-serif;
    font-weight: 500;
    margin-left: 600px;
  }

</style>
