<template>
  <label :for="name">{{ label }}:</label>
  <input type="text" :name="name" :id="name" @input="updateValue" />
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "InputText",
  props: {
    name: String,
    label: String,
    value: String,
    updateValue: Function
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
  margin-bottom: 1rem;
}
</style>
