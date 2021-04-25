<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p v-for="concert in sortedConcerts">
      {{ concert.date }}
      {{ concert.name }}
      {{ concert.venue }}
      {{ concert.tickets }}
      </p>
      <router-link v-bind:to="`${this.$route.params.id}/all`"> See More </router-link>
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
      xlConcerts: [],
      largeConcerts: [],
      sortedConcerts: [],
    };
  },
  created: function () {
    axios.get(`api/concerts/${this.$route.params.id}`).then((response) => {
      console.log("doing the concerts index");
      console.log(response.data);
      this.concerts = response.data;
      this.largeConcerts = this.concerts.filter((concert) => concert.category === "Large");
      console.log(this.largeConcerts);
      this.largeConcerts = this.largeConcerts.sort((a, b) => (a.score > b.score ? -1 : 1));
      console.log(this.largeConcerts);
      this.xlConcerts = this.concerts.filter((concert) => concert.category === "XL");
      console.log(this.xlConcerts);
      this.xlConcerts = this.xlConcerts.sort((a, b) => (a.score > b.score ? -1 : 1));
      console.log(this.xlConcerts);
      this.sortedConcerts.push(
        this.largeConcerts[0],
        this.largeConcerts[1],
        this.largeConcerts[2],
        this.largeConcerts[3],
        this.largeConcerts[4],
        this.xlConcerts[0],
        this.xlConcerts[1],
        this.xlConcerts[2],
        this.xlConcerts[3],
        this.xlConcerts[4]
      );
      this.sortedConcerts.sort((a, b) => (a.date > b.date ? 1 : -1));
      console.log(this.sortedConcerts);
    });
  },
  methods: {
    allConcerts: function () {
      console.log(this.concerts);
    },
  },
};
</script>

