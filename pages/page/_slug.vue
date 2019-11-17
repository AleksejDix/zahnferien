<template>
  <div>{{$data}}</div>
</template>

<script>
export default {
 async asyncData({ params, app, payload, route, store }) {
    const post = await import("~/content/pages/page/" + params.slug + ".json");
    return post;
  },
}
</script>

<style>

</style>
