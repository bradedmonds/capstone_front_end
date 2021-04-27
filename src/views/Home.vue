<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div class="dropdown">
      <button class="btn btn-secondary dropdown-toggle" type="button" id="dropdownMenuButton1" data-bs-toggle="dropdown" aria-expanded="false">
       Select Your City
      </button>
      <ul class="dropdown-menu" aria-labelledby="dropdownMenuButton1">
       <li v-for="city in cities"><router-link v-bind:to="`/${city.city}`" class="dropdown-item" href="/`${city.city}`">{{city.city}}</router-link></li>
      </ul>
    </div>
    <!-- <div v-for="city in cities"> 
      <router-link v-bind:to="`/${city.city}`">{{ city.city}} </router-link>
      </div> -->
  </div>
</template>

<style>
body {
  background-image: url("~@/assets/background.jpg");
  background-size: cover;
  outline: 2px, black;
}
h1 {
  margin: auto;
  position: absolute;
  top: 25%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
  font-size: 5em;
  color: white;
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande", "Lucida Sans", Arial, sans-serif;
  text-shadow: 0 0 4px black, 0 0 4px black, 0 0 4px black, 0 0 4px black, 0 0 4px black;
}
.dropdown {
  margin: auto;
  position: absolute;
  top: 40%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
}
btn btn-secondary dropdown-toggle {
  color: white;
}
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "LocalScene",
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

