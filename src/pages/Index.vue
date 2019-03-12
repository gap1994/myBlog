<template>
  <Layout :show-logo="false">
    <!-- Author intro -->
    <Author :show-title="true" />
    
    <!-- List posts -->
    <div class="posts">
      <PostCard v-for="edge in $page.posts.edges" :key="edge.node.id" :post="edge.node"/>
    </div>
    <Pager class="pagination" :linkClass="'pager'" :info="$page.posts.pageInfo"/>
  </Layout>
</template>

<script>
import { Pager } from 'gridsome'
import Author from '~/components/Author.vue'
import PostCard from '~/components/PostCard.vue'
export default {
  components: {
    Author,
    PostCard,
    Pager
  },
  metaInfo: {
    meta: [
      { name: 'author', content: 'gap1994' },
      { key: 'keywords', name: 'keywords', content: 'gap1994个人博客' },
      { key: 'description', name: 'description', content: 'gap1994个人博客' }
    ],
    title: 'gap1994'
  }
}
</script>
<page-query>
query ($page: Int) {
  posts: allPost (perPage: 10, page: $page) @paginate  {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        id
        title
        path
        tags {
          id
          title
          path
        }
        date (format: "YYYY-MM-DD")
        timeToRead
        description
        coverImage (width: 770, height: 380, blur: 10)
        ...on Post {
            id
            title
            path
        }
      }
    }
  }
}
</page-query>
<style lang="scss" scoped>
.home-links a {
  margin-right: 1rem;
}
.pagination{
  max-width: var(--content-width);
  margin: 0 auto;
  text-align: center;
  user-select: none;
}
.pager{
  margin: 0 5px;
  background-color: #fff;
  border-radius: 2px;
  padding: 0 4px;
  vertical-align: top;
  display: inline-block;
  font-size: 13px;
  min-width: 35.5px;
  height: 28px;
  line-height: 28px;
  cursor: pointer;
  box-sizing: border-box;
  text-align: center;
}
.active{
  background-color: var(--link-color);
  color: #fff!important;
}
</style>
