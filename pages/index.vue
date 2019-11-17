<template>
  <section>
    <h1 class="title">Zahnferien mit Lidia Dix</h1>
    <hr class="border-t-4 border-blue-500 rounded my-6">

    <ul v-if="list.length > 0" class="owl-y">
      <li v-for="post in list" :key="post.slug" class="py-6">
        <PostPreview :post="post"/>
      </li>
    </ul>

  </section>
</template>

<script>
import PostPreview from '~/components/PostPreview'

export default {
  components: {
    PostPreview,
  },
  async asyncData() {
    const files = await require.context('~/content/blog/article/', false, /\.json$/)
    const list = files
      .keys()
      .map(key => {
        const res = files(key);
        console.log(key)
        res.slug = key.slice(2, -5);
        return res;
      });
    return {
      list
    }
  }
}
</script>
