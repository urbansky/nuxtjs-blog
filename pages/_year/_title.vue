<template>
  <div>
    <nuxt-link to="/">Zurück</nuxt-link>
    <p v-html="post.html"/>
  </div>
</template>

<script>
  import hljs from 'highlight.js'
  import 'highlight.js/styles/darcula.css'

  export default {
    name: "Blogpost",
    async asyncData({ params }) {
      const post = await import(`../../post/${params.year}/${params.title}.md`);
      return { post }
    },
    mounted () {
      document.querySelectorAll('pre code').forEach((block) => {
        hljs.highlightBlock(block)
      })
    }
  }
</script>
