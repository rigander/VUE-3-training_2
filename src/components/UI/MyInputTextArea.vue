<template>
  <textarea
      :value="modelValue"
      @input="updateInput"
      class="input"
      >
  </textarea>
</template>

<script>
export default {
  name: "MyInputTextArea",
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
textarea {
  resize: none;
  width: 370px;
  height: 120px;
  padding: 5px;
  margin-top: 5px;
  background-color: rgb(204, 186, 105);
  border: none;
  border-radius: 1px;
  color: #000;
}
textarea::placeholder{
  color: #2768a9;
  font-size: 12px;
}
</style>