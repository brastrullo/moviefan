<template>
  <label :for="name">{{ label }}</label>
  <input v-model="query" type="text" :name="name" :id="name" />
  <p>{{ query }}</p>
  <button @click="searchMovie">Search</button>

  <ul>
    <li v-for="movie in moviesSelected" :key="movie.id">
      <article>
        {{ movie }}
      </article>
      <button>x</button>
    </li>
  </ul>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Movies",
  data() {
    return {
      query: "",
      moviesFound: [],
      moviesSelected: [{ id: 0, name: "movie1" }],
    };
  },
  props: {
    name: String,
    label: String,
  },
  methods: {
    async searchMovie() {
      const query = this.query;
      console.log(query)
      const API_KEY = `ea9385095138c0c18e3aca7590507b54`;
      const BASE_URL = `https://api.themoviedb.org/3/search/movie`;
      const FETCH_URL = `${BASE_URL}?api_key=${API_KEY}&query=${encodeURIComponent(query)}&page=1`;
      let res = await fetch(FETCH_URL);
      let data = await res.json();
      console.log(data)
    },
  },
});
</script>

<style lang="scss" scoped>
label {
  text-align: left;
}

input {
  background: none;
  border: none;
  border-bottom: 1px solid #333;
}
button {
  margin: 0.5em 0;
}
</style>
