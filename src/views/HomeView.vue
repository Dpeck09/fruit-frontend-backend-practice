<script>
import axios from "axios";
  export default {
    data: function () {
      return {
        message: "Welcome to Vue.js you filthy animals",
        fruits: []
      };
    },
    created: function () {
      this.indexFruits()
    },
    methods: {
      indexFruits: function () {
        axios.get("/fruits").then((response) => {
          console.log("fruits index", response);
          this.fruits = response.data
        });
      },
    },
  };
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h2>All Fruits</h2>
    <div v-for="fruit in fruits" v-bind:key="fruit.id">
    <h2>{{ fruit.name }}</h2>
    </div>

  </div>
</template>

<style></style>