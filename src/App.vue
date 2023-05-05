<template>
  <div class="app">
    <h1>Posts page</h1>
    <my-button>Получить посты</my-button>
    <my-button class="button" @click="showDialog">Create post</my-button>
    <post-list
        @remove="removePost"
        :posts="posts"
    />
    <my-dialog v-model:shown="dialogVisible">
      <post-form @create="addPost"/>
    </my-dialog>
  </div>

</template>

<script>
import PostList from "@/components/PostList.vue";
import PostForm from "@/components/PostForm.vue";
import MyDialog from "@/components/UI/MyDialog.vue";
import MyButton from "@/components/UI/MyButton.vue";
import axios from "axios";
export default {
  components: {MyButton, MyDialog, PostList, PostForm},
  data() {
    return {
      posts: [
        {id: 1, title: 'JavaScript', body: 'Описание поста 1'},
        {id: 2, title: 'JavaScript', body: 'Описание поста 2'},
        {id: 3, title: 'JavaScript', body: 'Описание поста 3'},
        {id: 4, title: 'JavaScript', body: 'Описание поста 4'},
      ],
      dialogVisible: false
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
    async fetchUsers() {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
      } catch (e) {
        console.log(e)
      }
    }
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

</style>