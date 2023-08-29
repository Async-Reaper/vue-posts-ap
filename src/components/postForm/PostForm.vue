<template>
    <form class="form" @submit.prevent>
      <h4>Добавление поста</h4>
      <Input
          v-model="post.title"
          type="text"
          placeholder="Название"
      />
      <Input
          v-model="post.body"
          type="text"
          placeholder="Описание"
      />
      <Button @click="createPost" class="btn">Создать</Button>
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
      createPost() {
        this.post.id = Date.now();
        this.$emit('create', this.post);
        this.post = {
          title: '',
          body: ''
        };
      },
    }
  }
</script>

<style scoped>
  .form {
    display: flex;
    flex-direction: column;
  }

</style>