<template>
  <form
      class="form"
      @submit.prevent
  >
    <h4>Creating post</h4>
    <my-input
        v-model="post.title"
        placeholder="Enter title"
    />
    <my-input
        v-model="post.body"
        placeholder="Enter description"
    />
    <my-button
        class="button"
        @click="addPost"
    >
      Create
    </my-button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: ''
      }
    }
  },
  methods: {
    addPost() {
      this.post.id = Date.now()
      this.$emit('create', this.post)
      this.post = {
        title: '',
        body: ''
      }
    },
  }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
}
.button {
  margin-top: 15px;
}
</style>