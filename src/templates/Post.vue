<template>
    <Layout>
        <!-- Back to Blog Button -->
        <g-link to="/blog/"><button class="text-blue-500">&larr; Back</button></g-link>

        <article>

        <!-- Title + Date -->
        <div class="my-6">
            <h1 class="text-xl mb-2" v-html="$page.post.title"/>
            <p v-html="$page.post.date" class="text-gray-600"/>
            <hr class="my-2">
        </div>

        <!-- Blog Post -->
        <div v-html="$page.post.content" class="space-y-6"/>
        </article>

    </Layout>
</template>

<script>
export default {
    metaInfo() {
        return {
            title: this.$page.post.title,
            meta: [{   
                // Meta Description
                key: 'description',
                name: 'description',
                content: this.$page.post.description
            }]
        }
    },
}
</script>

<page-query>
query Post ($path: String!) {
   post: post (path: $path) {
    id
    title
    content
    date (format: "D MMMM YYYY")
    timeToRead
  }
}
</page-query>

<style>
/* Apply Global Article Styles Here */
article h2 {
    @apply text-xl font-bold;
}

article a {
    @apply font-semibold text-blue-500;
}
</style>