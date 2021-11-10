<template>
  <div class="app">
    <b-container>
      <b-row>
        <header class="header">
          <search-form @update-search-query="val => searchQuery = val"/>
        </header>

        <section class="posts">
          <posts-list v-if="foundPosts.length > 0" :posts="foundPosts" :users="users"/>
          <b-alert v-else show variant="warning">Посты не найдены</b-alert>
        </section>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import axios from 'axios'

import SearchForm from "@/components/SearchForm";
import PostsList from "@/components/PostsList";

export default {
  name: 'App',
  components: {
    PostsList,
    SearchForm
  },
  async mounted() {
    const posts = await axios.get('http://jsonplaceholder.typicode.com/posts');
    const users = await axios.get('http://jsonplaceholder.typicode.com/users');

    this.posts = posts.data;
    this.users = users.data;
  },
  data() {
    return {
      posts: [],
      users: [],
      searchQuery: ''
    }
  },
  computed: {
    foundPosts() {
      if (this.searchQuery.length > 0) {
        const filteredUsers = this.users.filter(user => user.name.toLowerCase().includes(this.searchQuery.toLowerCase()))

        return  this.posts.filter(post => filteredUsers.some(user => user.id === post.userId))
      }

      return this.posts;
    },
  }
}
</script>

<style lang="scss">
.app {
  background: #ECF1F6;
  min-height: 100vh;
  overflow: hidden;
}

.header {
  padding: 40px 0;
}
</style>
