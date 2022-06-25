<template>
  <div class="app">
    <Navbar></Navbar>
    <router-view></router-view>
  </div>
</template>

<script>
import Navbar from "@/components/Navbar"
export default {
  name: "App",
  components: {Navbar}
}
</script>

<style scoped>
*{
  margin: 4px;
  padding: 0;
  box-sizing: border-box;
  background-color: #2b2b2b;
  color: bisque;
}
</style>