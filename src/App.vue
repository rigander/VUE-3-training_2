<template>
  <div class="app">
    <h1>Posts Page</h1>
    <my-button
        @click="showDialog"
    >Create Post
    </my-button>
    <my-dialog v-model:show="dialogVisible">
      <PostForm
          @create="createPost"
      />
    </my-dialog>
    <PostList
        :posts="posts"
        @remove="removePost"
        v-if="!isPostsLoading"
    />
    <div class="loading" v-else >LOADING....</div>
  </div>

</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyButton from "@/components/UI/my-button";
import MyDialog from "@/components/MyDialog";
import axios from 'axios';
export default {
  components: {
    MyButton,
    PostList,
    PostForm,
    MyDialog
  },
  name: "App",
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false
    }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true;
        setTimeout(async () => {
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
          this.posts = response.data;
          this.isPostsLoading = false;
        }, 2000)
      } catch (e) {
        alert ('Error')
      } finally {

      }
    }
  },
  mounted() {
    this.fetchPosts()
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
  .loading{
    color: red;
    font-size: 28px;
    font-weight: bold;
    margin: 10% 40%;
  }
</style>