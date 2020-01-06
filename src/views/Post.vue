<template>
  <div>
    Posts
    <div v-for="post in posts" :key="post.title">
      <div>ID: {{ post.id }}</div>
      <div>Title: {{ post.title }}</div>
      <div><router-link :to="{ name: 'postsWithId', params: { id: post.id }}">Detail</router-link></div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios'

export default {
  name: 'home',
  
  components: {
  },

  data() {
    return {
      posts: []
    }
  },

  mounted () {
    this.indexPosts()
  },

  methods: {
    async indexPosts () {
      const response = await axios.get('https://jsonplaceholder.typicode.com/posts')
      // eslint-disable-next-line no-console
      console.log('indexPosts', response.data)
      this.posts = response.data
      // eslint-disable-next-line no-console
      console.log('indexPosts', this.posts)
      this.$store.commit('setPosts', response.data)
    }
  },
}
</script>
