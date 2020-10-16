<template>
  <div class="home">
    <input-text
      ref="firstname"
      name="firstname"
      label="First Name"
      :value="firstname"
      :updateValue="updateFirstName"
    />
    <input-text
      ref="lastname"
      name="lastname"
      label="Last Name"
      :value="lastname"
      :updateValue="updateLastName"
      v-if="firstname"
    />
    <input-text-area
      ref="shortbio"
      name="shortbio"
      label="Short Bio"
      :value="shortbio"
      :updateValue="updateShortBio"
      v-if="lastname"
    />
    <movies
      v-if="shortbio"
      name="searchmovie"
      label="Add Favourite Movies (3 - 15)"
    />
  </div>
  <footer>
    <span class="tmdb-icon">+</span>
    powered by
    <span class="tmdb-name">TMDB</span>
  </footer>
</template>

<script lang="ts">
import { defineComponent, nextTick } from "vue";
import InputText from "@/components/InputText.vue";
import InputTextArea from "@/components/InputTextArea.vue";
import Movies from "@/components/Movies.vue";
import debounce from "lodash.debounce";
import throttle from "lodash.throttle";

export default defineComponent({
  name: "Home",
  data() {
    return {
      firstname: "",
      lastname: "",
      shortbio: "",
      firstnameInput: this.$refs.firstname,
      lastnameInput: this.$refs.lastname,
      shortbioInput: this.$refs.shortbio
    };
  },
  mounted() {
    this.$nextTick(() => {
      if (this.lastnameInput) {
        this.focusOnLastnameInput();
      }
    });
  },
  methods: {
    focusOnLastnameInput() {
      this.$el.lastnameInput.focus();
    },
    updateFirstName: debounce(async function(this: any, e: Event) {
      const target = e.target as HTMLInputElement;
      this.firstname = target.value;
    }, 300),
    updateLastName: debounce(function(this: any, e: Event) {
      const target = e.target as HTMLInputElement;
      this.lastname = target.value;
    }, 300),
    updateShortBio: throttle(function(this: any, e: Event) {
      const target = e.target as HTMLInputElement;
      this.shortbio = target.value;
    }, 200)
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
