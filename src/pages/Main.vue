<template>
  <div>
    <h1>Welcome to Vue training course</h1>
    <router-link class="links" to="/pages">Posts</router-link>
    <br>
    <router-link class="links" to="/about">About</router-link>
  </div>
</template>

<script>
export default {
  name: "Main"
}
</script>
<style scoped>
div{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.links{
  min-width: 85px;
  text-align: center;
  color: #dbd9da;
  padding: 3px;
  font-size: 28px;
  text-decoration: none;
  border: 2px solid #d6d6d6;
  border-radius: 4px;
}
.links:hover{
  color: burlywood;
  border-color: #de87bb;
}
</style>