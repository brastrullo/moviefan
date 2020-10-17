<template>
  <label :for="name">{{ label }}:</label>
  <textarea :name="name" :id="name" @input="updateValue" />
  <span v-if="value.length > 0">(character count: {{ value.length }})</span>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "InputTextArea",
  props: {
    name: String,
    label: String,
    value: String,
    updateValue: Function,
  },
});
</script>

<style lang="scss" scoped>
label {
  text-align: left;
}

textarea {
  background: none;
  border: 1px solid #333;
  margin: 1rem 0;
}
</style>
