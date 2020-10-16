<template>
  <label :for="name">{{ label }}</label>
  <input type="text" :name="name" :id="name" />
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
  name: "SearchMovie",
  data() {
    return {
      moviesFound: [],
      moviesSelected: [{ id: 0, name: "movie1" }]
    };
  },
  props: {
    name: String,
    label: String
  }
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
</style>
