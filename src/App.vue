<template>
  <div class="app">
    <h1>Posts page</h1>
    <my-button class="button" @click="showDialog">Create post</my-button>
    <post-list
        v-if="!isPostsLoading"
        @remove="removePost"
        :posts="posts"
    />
    <div v-else>Loading...</div>
    <my-dialog v-model:shown="dialogVisible">
      <post-form @create="addPost"/>
    </my-dialog>
  </div>
</template>

<script>
import PostList from "@/components/PostList.vue";
import PostForm from "@/components/PostForm.vue";
import axios from "axios";
export default {
  components: { PostList, PostForm },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostsLoading: false
    }
  },
  methods: {
    addPost(post) {
      this.posts.push(post)
      this.dialogVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter(p => {
        return p.id !== post.id
      })
    },
    showDialog() {
       this.dialogVisible = true
    },
    async fetchPosts() {
      try {
        this.isPostsLoading = true
        setTimeout(async() => {
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
          this.posts = response.data
          this.isPostsLoading = false
        }, 2000)
      } catch (e) {
        console.log(e)
      } finally {
        // this.isPostsLoading = false
      }
    }
  },
  mounted() {
    console.log("MOUNTED")
    this.fetchPosts()
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
.button {
  margin: 20px 0;
}
.button:first-of-type {
  margin-right: 10px;
}

</style>