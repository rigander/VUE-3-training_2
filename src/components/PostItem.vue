<template>
  <div class="post">
    <div>
      <div>{{ post.id }}</div>
      <div><strong>Name : </strong>{{ post.title }}</div>
      <div class="post-body"><strong>Description : </strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
      <my-button
       @click="$emit('remove', post)"
      >Delete Post
      </my-button>
    </div>
  </div>
</template>

<script>
import MyButton from "@/components/UI/my-button";
export default {
  name: "PostItem",
  components: {MyButton},
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
  padding: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.post-body{
  padding-right: 220px;
}
</style>