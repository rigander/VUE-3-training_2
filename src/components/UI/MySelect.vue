<template>
  <select
        v-model="modelValue"
        @change="changeOption"
        name="" id="">
    <option disabled value="">Choose from list</option>
    <option
        v-for="option in options"
        key="option.value"
        :value="option.value"
    >
        {{ option.name }}
    </option>
  </select>
</template>

<script>
export default {
  name: "MySelect",
  props: {
    modelValue: {
      type: String
    },
    options: {
      type: Array,
      default: () => []
    }
  },
  methods: {
    changeOption(event) {
      this.$emit('update:modelValue', event.target.value);
    }
  }
}
</script>

<style scoped>
  select{
    margin-right: 20px;
    background-color: #2768a9;
    color: #2b2b2b;
    font-size: 18px;
    min-width: 250px;
    border-radius: 5px;
  }
  option{
    background-color: #7fa8cc;
    color: #000;
    font-weight: bold;
  }
</style>