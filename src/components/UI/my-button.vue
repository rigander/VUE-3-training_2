<template>
<button>
  <slot></slot>
</button>
</template>

<script>
export default {
  name: "my-button"
}
</script>

<style scoped>
button {
  padding: 5px;
  margin-top: 5px;
  border-radius: 2px;
  border: #2768a9;
  background-color: bisque;
  color: #2768a9;
  align-self: flex-end;
}
button:active {
  background-color: #2768a9;
  color: darkgoldenrod;
}
</style>