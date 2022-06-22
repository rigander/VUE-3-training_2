<template>
  <div class="app">
    <input type="text" v-model.number="title">
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
    />
  </div>

</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyButton from "@/components/UI/my-button";
import MyDialog from "@/components/MyDialog";
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
      title: '',
      posts: [
        {id:1, title: 'Javascript', body: 'Post description'},
        {id:2, title: 'Javascript 2', body: 'Post description 2'}
      ],
      dialogVisible: false,
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