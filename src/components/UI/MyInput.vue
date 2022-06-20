<template>
  <input :value="modelValue" @input="updateInput" class="input" type="text">
</template>

<script>
export default {
  name: "MyInput",
  props: {
    modelValue: [String, Number],

  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
}
</script>

<style scoped>
.input {
  width: 100%;
  padding: 5px;
  margin-top: 5px;
  background-color: rgb(204, 186, 105);
  border: none;
  border-radius: 1px;
  color: #000;
}
.input::placeholder{
  color: #2768a9;
  font-size: 11px;
}
</style>