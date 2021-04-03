<template>
  <Layout>
    <!-- Learn how to use images here: https://gridsome.org/docs/images -->
    <g-image alt="Example image" src="~/favicon.png" width="135" />

    <h1 class="blog-title">
      Welcome my experimental mock-blog
    </h1>

    <p>A magical place where I write all sorts of mock-content.</p>

    <p class="home-links">
      <a href="https://gridsome.org/docs/" target="_blank" rel="noopener">Gridsome Docs</a>
      <a href="https://github.com/gridsome/gridsome" target="_blank" rel="noopener">GitHub</a>
    </p>

    <div class="articles-list">
      <h2 class="article-list__section-heading">New Articles</h2>
      <!-- articles will be listed here -->

      <div class="article-list__item" v-for="({ node: article }, index) in $page.allBlogPost.edges" :key="index">
        <h3>
          <g-link :to="article.path">{{ article.title }}</g-link>
          <!-- g-link is the Gridsome equivalent of router-link for Vue, but with some magic  ✨ -->
        </h3>
        <p>
          Published on <strong>{{ article.date }}</strong>
        </p>
        <p>{{ article.description }}</p>
      </div>

    </div>
  </Layout>
</template>

<page-query>
query {
  allBlogPost (filter:{ published: {eq: true } } ) {
    edges{
      node{
        path,
        title,
        date(format: "DD MMM YYYY"),
        timeToRead,
        description,
        content,
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!'
  }
}
</script>

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
