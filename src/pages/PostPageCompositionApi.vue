<template>
  <div>
    <h1>{{ likes }}</h1>
    <button @click = "addLike"
    >Add Like</button>
    <br>
    <button @click = "disLike"
    >Remove Like</button>
    <h1>Posts Page</h1>
<!--    <my-input-->
<!--        v-focus-->
<!--        v-model="searchQuery"-->
<!--        placeholder="Search..."-->
<!--    />-->
<!--    <div class="app__btns">-->
<!--      <my-button-->
<!--          @click="showDialog"-->
<!--      >Create Post-->
<!--      </my-button>-->
<!--      <my-select-->
<!--          v-model="selectedSort"-->
<!--          :options="sortOptions"-->
<!--      />-->
<!--    </div>-->
<!--    <my-dialog v-model:show="dialogVisible">-->
<!--      <PostForm-->
<!--          @create="createPost"-->
<!--      />-->
<!--    </my-dialog>-->
<!--    <PostList-->
<!--        :posts="sortedAndSearchedPosts"-->
<!--        @remove="removePost"-->
<!--        v-if="!isPostsLoading"-->
<!--    />-->
<!--    <div class="loading" v-else >LOADING....</div>-->
<!--    <div v-intersection="loadMorePosts" class="observer"></div>-->
  </div>

</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyButton from "@/components/UI/my-button";
import MyDialog from "@/components/MyDialog";
import axios from 'axios';
import MySelect from "@/components/UI/MySelect";
import {ref} from "vue";

export default {
  components: {
    MySelect,
    MyButton,
    PostList,
    PostForm,
    MyDialog,
  },
  name: "PostPage",
  data() {
    return {
      dialogVisible: false,
      sortOptions: [
        {value: 'title', name: 'By name'},
        {value: 'body', name: 'By content'},
      ]
    }
  },
  setup(props) {
    const likes = ref(100)
    console.log(likes)
    const addLike = () => {
      likes.value += 4
    }
    const disLike = () => {
      likes.value -= 4
    }
    return {
      likes,
      addLike,
      disLike
    }
  }
}
</script>

<style>


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
.page__wrapper {
  display: flex;
  margin-top: 15px;
}
.page {
  border: 1px solid black;
  padding: 10px;
}
.current_page {
  border: 2px solid green;
}
</style>