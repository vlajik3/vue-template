<template>
  <button class="button">
<slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button'
}
</script>

<style scoped>

.button {
  align-self: flex-end;
  border: 1px solid lawngreen;
  border-radius: 5px;
  color: #427016;
  background: none;
  padding: 10px 15px;
  transition: all 0.1s;
}
.button:hover {
  background: rgba(124, 252, 0, 0.5);
  cursor: pointer;
}
</style>