<template>
  <div class="post">
    <div><strong>Название:</strong> {{post.title}}</div>
    <div><strong>Описание:</strong> {{post.body}}</div>
    <div class="post__buttons">
      <my-button @click="$emit('remove', post)">Delete</my-button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    post: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.post {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 15px;
  border: 1px solid lawngreen;
  border-radius: 10px;
  margin-top: 15px;
}
</style>