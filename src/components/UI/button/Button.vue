<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "Button"
}
</script>

<style scoped>
  .btn {
    margin-top: 15px;
    padding: 10px 15px;
    align-self: flex-end;
    backdrop-filter: none;
    border-radius: 5px;
    color: teal;
    border: 1px solid teal;
    cursor: pointer;
  }
</style>