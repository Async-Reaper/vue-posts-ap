<template>
  <div v-if="posts.length > 0">
    <h3>Список пользователей</h3>
    <post-item
        @remove="$emit('remove', post)"
        :key="post.id"
        :post="post"
        v-for="post in posts"
    />
  </div>
  <h2 v-else>Список постов пуст</h2>
</template>

<script>
  import PostItem from "@/components/postItem/PostItem";
  export default {
    components: {PostItem},
    props: {
      posts: {
        type: Array,
        required: true
      }
    }
  }
</script>

<style scoped>

</style>