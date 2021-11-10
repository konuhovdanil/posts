<template>
  <div class="post mb-4">
    <div class="post__title text-primary mb-3">{{ post.title }}</div>
    <div class="post__description text-secondary mb-3">{{ post.body }}</div>
    <div class="post__author text-muted">{{ user.name }}</div>
  </div>
</template>

<script>
export default {
  name: "Post",
  props: {
    post: Object,
    user: Object
  },
}
</script>

<style scoped lang="scss">
.post {
  background: #fff;
  padding: 20px;
  border-radius: 8px;
}
</style>