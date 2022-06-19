<template>
  <div class="post">
    <div>
      <div><strong>Name : </strong>{{ post.title }}</div>
      <div><strong>Description : </strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
      <my-button

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
  padding: 5px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
</style>