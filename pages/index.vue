<template>
  <div>
    <h1>Liste der Blogbeiträge</h1>
    <ul>
      <li v-for="post in posts">
        <nuxt-link :to="post.link">{{ post.attributes.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>

  export default {
    asyncData() {
      const resolve = require.context('~/post', true, /\.md$/);
      const posts = resolve.keys().map((key) => {
        return {
          link: key.slice(0, -3),
          attributes: resolve(key).attributes
        }
      });
      return { posts }
    }
  }
</script>
