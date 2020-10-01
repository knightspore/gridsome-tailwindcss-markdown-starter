<template>
    <Layout>

    <h1 class="text-xl mb-2">Welcome to your Blog!</h1>

    <div class="space-y-4">
      <BlogFeedPost 
      v-for="edge in $page.allPost.edges" 
      :key="edge.node.id" 
      :post="edge.node"/>
    </div>

    </Layout>
</template>

<page-query>
query {
  allPost {
    edges {
      node {
        id
        title
        date (format: "D MMMM YYYY")
        path
        description
      }
    }
  }
}
</page-query>

<script>
import BlogFeedPost from '@/components/BlogFeedPost'

export default {
  components: {
    BlogFeedPost,
  },
  metaInfo: {
    title: 'Blog'
  }
}
</script>
