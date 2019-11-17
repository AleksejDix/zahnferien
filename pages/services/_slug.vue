<template>
  <div>{{$data}}</div>
</template>

<script>
export default {
 async asyncData(context) {
    const post = await import("~/content/services/service/" + context.params.slug + ".json");
    return post;
  },
}
</script>

<style>

</style>
