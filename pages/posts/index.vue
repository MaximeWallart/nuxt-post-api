<template>
  <div>
    <h1>Liste des posts</h1>
    <ul>
      <li v-for="post in posts" :key="post.id">
        <nuxt-link :to="`/posts/${post.id}`">
          {{ post.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  async asyncData ({ $axios }) {
    const posts = await $axios.$get(
      'https://jsonplaceholder.typicode.com/posts'
    )

    return { posts }
  }
}
</script>

<style>
template {
  background-color: white;
}
</style>
