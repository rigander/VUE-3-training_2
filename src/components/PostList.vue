<template>
<div v-if="posts.length > 0 ">
  <h3>List of posts</h3>
  <transition-group name="post-list">
    <PostItem
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
    />
  </transition-group>
</div>
  <h2 v-else style="color: rgba(255,166,0,0.74)">
    List of posts is empty!
  </h2>
</template>

<script>
import PostItem from "@/components/PostItem";
export default {
  name: "PostList",
  components: {PostItem},
  props: {
    posts: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.post-list-item {
  display: inline-block;
  margin-right: 10px;
}
.post-list-enter-active, .post-list-leave-active {
  transition: all 0.4s;
}
.post-list-enter, .post-list-leave-to /* .post-list-leave-active до версии 2.1.8 */ {
  opacity: 0;
  transform: translateX(130px);
}
.post-list-move {
  transition: transform 0.4s ease;
}
</style>