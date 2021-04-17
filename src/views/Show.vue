<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p v-for="concert in concerts">
      {{ concert.date }}
      {{ concert.name }}
      {{ concert.venue }}
      {{ concert.tickets }}
      </p>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";
export default {
  data: function () {
    return {
      message: `${this.$route.params.id} Concerts`,
      concerts: [],
    };
  },
  created: function () {
    axios.get(`api/cities/${this.$route.params.id}`).then((response) => {
      console.log("doing the show");
      console.log(response.data);
      this.concerts = response.data;
    });
  },
  methods: {},
};
</script>

