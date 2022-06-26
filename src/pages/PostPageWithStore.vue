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
        v-model="searchQuery"
        placeholder="Search..."
    />
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
      posts: [],
      dialogVisible: false,
      isPostsLoading: false,
      selectedSort: '',
      searchQuery: '',
      page: 1,
      limit: 10,
      totalPages: 0,
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
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?', {
          params: {
            _page: this.page,
            _limit: this.limit
          }
        });
        this.totalPages = Math.ceil(response.headers['x-total-count'] / this. limit)
        this.posts = response.data;
      } catch (e) {
        alert ('Error')
      } finally {
        this.isPostsLoading = false;
      }
    },
    async loadMorePosts() {
      try {
        this.page +=1;
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?', {
          params: {
            _page: this.page,
            _limit: this.limit
          }
        });
        this.totalPages = Math.ceil(response.headers['x-total-count'] / this. limit)
        this.posts = [...this.posts, ...response.data];
      } catch (e) {
        alert ('Error')
      } finally {
      }
    }
  },
  mounted() {
    this.fetchPosts();
    console.log(this.$refs.observer);
   },
  computed: {
    sortedPosts() {
      return [...this.posts].sort((post1, post2) => post1[this.selectedSort]?.localeCompare(post2[this.selectedSort]))
    },
    sortedAndSearchedPosts() {
      return this.sortedPosts.filter(post => post.title.toLowerCase().includes(this.searchQuery.toLowerCase()))
    }

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