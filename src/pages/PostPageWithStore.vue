<template>
  <div>
    <h1>
      {{ $store.state.isAuth ? "User Authorized" : "You need to Authorize to get access" }}
    </h1>
    <h1>{{ $store.getters.doubleLikes }}</h1>
    <my-button
        class="like_dislike"
        @click="$store.commit('incrementLikes')"
    >Like
    </my-button>
    <my-button
        class="like_dislike"
        @click="$store.commit('decrementLikes')"
    >Dislike
    </my-button>
    <my-input
        v-focus
        :model-value="searchQuery"
        @update:model-value="setSearchQuery"
        placeholder="Search..."
    />
    <div class="app__btns">
      <my-button
          @click="showDialog"
      >Create Post
      </my-button>
      <my-select
          :model-value="selectedSort"
          @update:model-value="setSelectedSort"
          :options="sortOptions"
      />
    </div>
    <my-dialog v-model:show="dialogVisible">
      <PostForm
          @create="createPost"
      />
    </my-dialog>
    <PostList
        :posts="sortedAndSearchedPosts"
        @remove="removePost"
        v-if="!isPostsLoading"
    />
    <div class="loading" v-else >LOADING....</div>
    <div v-intersection="loadMorePosts" class="observer"></div>
  </div>

</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyButton from "@/components/UI/my-button";
import MyDialog from "@/components/MyDialog";
import axios from 'axios';
import MySelect from "@/components/UI/MySelect";
import {mapState, mapMutations, mapActions, mapGetters} from 'vuex';

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
    }
  },
  methods: {
    ...mapMutations({
        setPage: 'post/setPage',
        setSearchQuery: 'post/setSearchQuery',
        setSelectedSort: 'post/setSelectedSort'
    }),
    ...mapActions({
        loadMorePosts: 'post/loadMorePosts',
        fetchPosts: 'post/fetchPosts'
    }),
    createPost(post) {
      this.posts.push(post);
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true;
    },
  },
  mounted() {
    this.fetchPosts();
   },
  computed: {
    ...mapState({
      posts: state => state.post.posts,
      isPostsLoading: state => state.post.isPostsLoading,
      selectedSort: state => state.post.selectedSort,
      searchQuery: state => state.post.searchQuery,
      page: state => state.post.page,
      limit: state => state.post.limit,
      totalPages: state => state.post.totalPages,
      sortOptions:state => state.post.sortOptions,
    }),
    ...mapGetters({
      sortedPosts: 'post/sortedPosts',
      sortedAndSearchedPosts: 'post/sortedAndSearchedPosts'
    })
  },
  watch: {
  },
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
.like_dislike{
  margin-right: 10px;
}
</style>