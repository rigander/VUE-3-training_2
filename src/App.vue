<template>
  <div class="app">
    <h1>Posts Page</h1>
    <div class="app__btns">
      <my-button
         @click="showDialog"
      >Create Post
      </my-button>
      <my-select
         v-model="selectedSort"
         :options="sortOptions"
      />
    </div>
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
import MySelect from "@/components/UI/MySelect";
export default {
  components: {
    MySelect,
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
      isPostsLoading: false,
      selectedSort: '',
      sortOptions: [
        {value: 'title', name: 'By name'},
        {value: 'body', name: 'By content'},

      ]
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
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10');
        this.posts = response.data;
      } catch (e) {
        alert ('Error')
      } finally {
        this.isPostsLoading = false;
      }
    }
  },
  mounted() {
    this.fetchPosts()
  },
  watch: {
    selectedSort(newValue) {
      console.log(newValue);
    },
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
  .app__btns{
    display: flex;
    justify-content: space-between;
  }
</style>