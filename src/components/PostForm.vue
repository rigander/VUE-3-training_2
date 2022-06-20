<template>
  <form @submit.prevent>
    <h4>Post Name</h4>
    <my-input
        v-model="post.title"
        type="text"
        placeholder="Post Name"
    />
    <my-input
        v-model="post.body"
        type="text"
        placeholder="Description"
    />
    <my-button
        @click="createPost"
    >
      Create Post
    </my-button>
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

</style>