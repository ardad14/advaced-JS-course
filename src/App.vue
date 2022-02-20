<template>
  <div class="hello">
    <TaskOne></TaskOne>
  </div>
  <hr>
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
  }
  img{
    width: 250px;
    height: 250px;
    padding-left: 35px;
  }
</style>
