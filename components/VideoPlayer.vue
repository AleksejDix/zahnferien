<template>
  <div class="w-full relative overflow-hidden rounded-lg" :style="{paddingTop: '56.5%'}">
    <iframe
      loading="lazy"
      class="w-full h-full absolute inset-0"
      type="text/html"
      allowfullscreen="allowfullscreen"
      :src="video"
      frameborder="0"
    />
   </div>
</template>

<script>
export default {
  props: ['video']
}
</script>
