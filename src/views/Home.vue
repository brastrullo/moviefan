<template>
  <div class="home">
    <input-text
      name="firstname"
      label="First Name"
      :value="firstname"
      :updateValue="updateFirstName"
    />
    <input-text
      name="lastname"
      label="Last Name"
      :value="lastname"
      :updateValue="updateLastName"
    />
    <input-text-area
      name="shortbio"
      label="Short Bio"
      :value="shortbio"
      :updateValue="updateShortBio"
    />
    <movies name="searchmovie" label="Add Favourite Movies (3 - 15)" />
  </div>
  <footer>
    <span class="tmdb-icon">+</span>
    powered by
    <span class="tmdb-name">TMDB</span>
  </footer>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import InputText from "@/components/InputText.vue";
import InputTextArea from "@/components/InputTextArea.vue";
import Movies from "@/components/Movies.vue";

export default defineComponent({
  name: "Home",
  data() {
    return {
      firstname: "",
      lastname: "",
      shortbio: ""
    };
  },
  methods: {
    updateFirstName(e: Event) {
      const target = e.target as HTMLInputElement;
      this.firstname = target.value;
    },
    updateLastName(e: Event) {
      const target = e.target as HTMLInputElement;
      this.lastname = target.value;
    },
    updateShortBio(e: Event) {
      const target = e.target as HTMLTextAreaElement;
      this.shortbio = target.value;
    }
  },
  components: {
    InputText,
    InputTextArea,
    Movies
  }
});
</script>

<style lang="scss" scoped>
.home {
  display: flex;
  flex-flow: column nowrap;
  margin: 0 auto;
  max-width: 30em;
}
footer {
  color: #2c3e50;
  .tmdb-name {
    color: #01b4e4;
  }
}
</style>
