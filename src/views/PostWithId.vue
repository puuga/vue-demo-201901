<template>
  <div>
    PostWithId {{ id }}
    <div>{{ post }}</div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'home',
  
  components: {
  },

  data() {
    return {
    }
  },

  computed: {
    id () {
      return this.$route.params.id
    },
    post () {
      return this.$store.state.posts.find(post => post.id === this.id)
    }
  },
}
</script>
