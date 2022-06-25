<template>
  <form @submit.prevent>
    <h4>Create New Post</h4>
    <br>
    <my-input
        v-focus
        v-model="post.title"
        type="text"
        placeholder="Post Name"
    />
    <my-input-text-area
        v-model="post.body"
        type="text"
        placeholder="Description"
    />
    <br>
    <my-button
        @click="createPost"
    >
      Create Post
    </my-button>
  </form>
</template>

<script>


import MyInputTextArea from "@/components/UI/MyInputTextArea";
export default {
  name: "PostForm",
  components: {MyInputTextArea},
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = Date.now();
      this.$emit('create', this.post, 'sec arg', 'third arg');
      this.post = {
        title: '',
        body: ''
      }
    },
  }
}
</script>

<style scoped>
form{
  display: flex;
  flex-direction: column;
  padding: 10px;
  background-color: #2768a9;
  border-radius: 5px;
}
h4{
  font-size: 22px;
  margin: 0;
}

</style>