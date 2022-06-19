<template>
  <form @submit.prevent>
    <h4>Post Name</h4>
    <input
        :value="post.title"
        @input="post.title = $event.target.value"
        class="input"
        type="text"
        placeholder="Post Name"
    >
    <input
        :value="post.body"
        @input="post.body = $event.target.value"
        class="input"
        type="text"
        placeholder="Description"
    >
    <button class="btn">Create Post</button>
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