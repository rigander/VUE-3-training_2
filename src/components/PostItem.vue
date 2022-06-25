<template>
  <div class="post">
    <div class="post__text">
      <div class="post__id">{{ post.id }}</div>
      <div><strong>Name : </strong>{{ post.title }}</div>
      <div class="post-body"><strong>Description : </strong>{{ post.body }}</div>
    </div>
    <div class="post__btns">
      <my-button
          @click="$router.push(`/pages/${post.id}`)"
      >Open Post
      </my-button>
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
  border-radius: 3px;
  margin-top: 15px;
  padding: 15px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.post__btns{
  height: 70px;
  width: 130px;
  margin-bottom: 20px;
}
.post__text{
  width: 740px;
}
.post__id{
  color:green;
  font-size: 24px;
  font-weight: bold;
}
</style>