<template>
  <div class="navbar">
    <div @click="$router.push('/')" class="vue3">Vue 3</div>
    <div class="navbar__btns">
      <my-button @click="$router.push('/pages')">Posts</my-button>
      <my-button @click="$router.push('/pages')">About</my-button>
      <my-button @click="$router.push('/store')">Store</my-button>
    </div>
  </div>

</template>

<script>
export default {
  name: "Navbar",
  components: {}
}
</script>

<style scoped>
.navbar{
  height: 50px;
  background-color: #2b2b2b;
  box-shadow: 2px 2px 4px yellowgreen;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 20px 15px 20px;
}
.navbar__btns{
  width: 400px;
  display: flex;
  justify-content: space-between;
}

</style>