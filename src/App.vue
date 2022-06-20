<template>
  <div class="app">
    <PostForm
        @create="createPost"
    />
    <PostList
        :posts="posts"
        @remove="removePost"
    />
  </div>

</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
export default {
  components: {
    PostList,
    PostForm
  },
  name: "App",
  data() {
    return {
      posts: [
        {id:1, title: 'Javascript', body: 'Post description'},
        {id:2, title: 'Javascript 2', body: 'Post description 2'}
      ],
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    }
  }
}
</script>

<style>
*{
  margin: 2px 2px;
  padding: 0;
  box-sizing: border-box;
  background-color: #2b2b2b;
  color: bisque;
}

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