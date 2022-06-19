<template>
  <div class="post" v-for="post in posts" >
    <div><strong>Name : </strong>{{post.title}}</div>
    <div><strong>Description : </strong>{{post.body}}</div>
  </div>
</template>

<script>
export default {
  name: "PostList",
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.post {
  border: 2px solid cadetblue;
  border-radius: 1px;
  margin-top: 15px;
  padding: 5px;
}
</style>