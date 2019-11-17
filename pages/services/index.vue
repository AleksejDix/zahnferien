<template>
  <div>
    <h1 class="title">Diensleistungen</h1>
    <hr class="border-t-4 border-blue-500 rounded my-6">
    {{$data}}
    <!-- <ul class="text-gray-700">
      <li v-for="item in list" class="mt-2">
        <Icon name="icon-check" class="mr-2"/> <span>{{item}}</span>
      </li>
    </ul> -->
  </div>
</template>

<script>
import Icon from '@/components/Icon'
export default {
  components: {
    Icon
  },
  data() {
    return {
      list: [],
    }
  },
  async asyncData() {
    const files = await require.context('~/content/services/service/', false, /\.json$/)
    const list = files
      .keys()
      .map(key => {
        const res = files(key);
        res.slug = key.slice(2, -5);
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
