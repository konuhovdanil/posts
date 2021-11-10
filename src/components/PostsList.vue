<template>
  <b-container>
    <b-row cols="1"cols-md="2" cols-lg="3">
      <b-col v-for="post in posts" :key="post.id">
        <post :post="post" :user="getUserById(post.userId)"/>
      </b-col>
    </b-row>
  </b-container>
</template>

<script>
import Post from "./Post";
export default {
  name: "PostsList",
  components: {
    Post
  },
  props: {
    posts: Array,
    users: Array
  },
  methods: {
    getUserById(userId) {
      const user = this.users.filter(user => user.id === userId)

      return user.length > 0 ? user[0] : {}
    }
  }
}
</script>

<style scoped>

</style>