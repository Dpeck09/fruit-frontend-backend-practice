<script>
import axios from "axios";
  export default {
    data: function () {
      return {
        message: "Welcome to Vue.js you filthy animals",
        fruits: [],
        newFruits: {},
        currentFruits: {}
      };
    },
    created: function () {
      this.indexFruits()
    },
    methods: {
      indexFruits: function () {
        axios.get("/fruits").then((response) => {
          console.log("fruits index", response);
          this.fruits = response.data;
        });
      },
      showFruits: function (fruit) {
        console.log('show')
        document.querySelector("#fruit-details").showModal();
        this.currentFruit = fruit;
      }
    },
  };
</script>

<template>
  <div class="home">

  <button v-on:click="showFruit(fruit)">More Info</button>

  <h1>{{ message }}</h1>
  <h2>All Fruits</h2>
  <br><br>
  <div v-for="fruit in fruits" v-bind:key="fruit.id">
  <h2>{{ fruit.name }}</h2>
  <img v-bind:src="fruit.image">
  <p>Color: {{ fruit.color }}</p>
  <br>
  </div>

  </div>
</template>

<style>
img {
  width: 30%;
}
</style>