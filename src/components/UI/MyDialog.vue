<template>
  <div class="dialog" v-if="shown" @click.stop="hideDialog">
    <div
        class="dialog__content"
        @click.stop
    >
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'my-dialog',
  props: {
    shown: {
      type: Boolean,
      default: false
    }
  },
  methods: {
    hideDialog() {
      this.$emit('update:shown', false)
    }
  }
}
</script>

<style scoped>
  .dialog {
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: rgba(0,0,0, 0.5);
    position: fixed;
    display: flex;
  }
  .dialog__content {
    margin: auto;
    background: #ffffff;
    border-radius: 10px;
    min-height: 50px;
    min-width: 300px;
    padding: 20px;
  }
</style>