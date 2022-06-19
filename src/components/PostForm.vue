<template>
  <form @submit.prevent>
    <h4>Post Name</h4>
    <input
        v-model="post.title"
        class="input"
        type="text"
        placeholder="Post Name"
    >
    <input
        v-model="post.body"
        class="input"
        type="text"
        placeholder="Description"
    >
    <button
        class="btn"
        @click="createPost"
    >
    Create Post
    </button>
  </form>
</template>

<script>
export default {
  name: "PostForm",
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
}
.input {
  width: 100%;
  border: 1px solid;
  padding: 5px;
  margin-top: 5px;
  background-color: rgb(204, 186, 105);
  border: none;
  border-radius: 1px;
  color: #000;
}
.input::placeholder{
  color: #2768a9;
  font-size: 11px;
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