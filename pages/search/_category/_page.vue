<template>
  <my-items :articleList="articleList"></my-items>
</template>
<script>
import MyItems from '~/components/Items.vue'
export default {
  name: 'search-category-page',
  async fetch ({ store, params }) {
    // 填充状态树
    await store.dispatch('LIST_PAGE', {
      typeName: 'search',
      category: params.category,
      page: params.page
    })
  },
  head () {
    return {
      title: `${this.$store.state.category} | vueblog`
    }
  },
  computed: {
    articleList () {
      return this.$store.state.articleList
    }
  },
  components: {
    MyItems
  }
}
</script>
