<template>
  <div>
    <p>(favourite movies)</p>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "FavouriteMovies",
  props: {
    list: Array
  }
});
</script>

<style lang="scss" scoped>

</style>
