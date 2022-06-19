<template>
  <div class="post">
    <div>
      <div><strong>Name : </strong>{{ post.title }}</div>
      <div><strong>Description : </strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
      <button>Delete Post</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "PostItem",
  props: {
    post: {
      type: Object,
      required: true,
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
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>