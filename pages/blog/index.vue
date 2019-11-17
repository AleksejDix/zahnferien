<template>
  <div>
     <h1 class="title">Blog – Wissenswertes</h1>
     <hr class="border-t-4 border-blue-500 rounded my-6">
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Blog"
    }
  },
  async asyncData() {
    const files = await require.context('~/content/blog/article/', false, /\.json$/)
    console.log(files)
    const list = files
      .keys()
      .map(key => {
        const res = files(key);
        res.slug = key.slice(2, -5); // remove ./ from beginnign and .json from the end
        return res;
      });
    return {
      list
    }
  }
}
</script>

<style>

</style>
