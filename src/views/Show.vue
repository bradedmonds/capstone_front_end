<template>
  <div class="home">
    <h1>{{ message }}</h1>
    
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: "Show Page",
      cities: [],
    };
  },
  created: function () {
    axios.get(`api/cities/${this.$route.params.id}`).then((response) => {
      console.log("doing the show");
      console.log(response.data);
      this.cities = response.data;
    });
  },
  methods: {},
};
</script>

