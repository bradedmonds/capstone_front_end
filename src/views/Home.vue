<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for="city in cities"> 
      <router-link v-bind:to="`/${city.city}`">{{ city.city}} </router-link>
      </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Welcome to Vue.js!",
      cities: [],
    };
  },
  created: function () {
    axios.get("api/cities").then((response) => {
      console.log("doing the cities index");
      console.log(response.data);
      this.cities = response.data;
    });
  },
  methods: {},
};
</script>

