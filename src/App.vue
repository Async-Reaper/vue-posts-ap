<template>
  <div class="App">
    <div class="app-btn">
      <Button @click="showDialog">Создать пост</Button>
      <Select :model-value="selectedSort"/>
    </div>
    <ModalWindow v-model:show="visibleModal">
      <PostForm @create="createPost" />
    </ModalWindow>
    <Button @click="getPosts">Получить посты</Button>
    <span v-if="isPostLoaded">Loaded</span>
    <PostList
      v-else
      :posts="posts"
      @remove="removePost"
    />
  </div>
</template>

<script>
  import PostForm from "@/components/postForm/PostForm";
  import PostList from "@/components/postList/PostList";
  import axios from "axios";
  import Select from "@/components/UI/select/Select";

  export default {
    components: {Select, PostList, PostForm},
    data() {
      return {
        visibleModal: false,
        posts: [],
        isPostLoaded: false,
        selectedSort: ''
      }
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.visibleModal = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((p) => p.id !== post.id);
    },
    showDialog() {
      this.visibleModal = true;
    },

    async getPosts() {
      try {
        this.isPostLoaded = true;
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts/?_limit=10');
        this.posts = response.data;
      } catch (e) {
        console.log(e)
      } finally {
        this.isPostLoaded = false
      }
    }
  },
    mounted() {
      this.getPosts()
    }
  }
</script>

<style>
  body {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  .App {
    padding: 20px;
  }

  .app-btn {
    display: flex;
    justify-content: space-between;
  }
</style>