<template>
  <div>
    <h1 class="title"> {{title}}</h1>
    <hr class="border-t-4 border-blue-500 rounded my-6">
    <ul class="text-gray-700">
      <li v-for="item in classic" class="mt-2">
        <Icon name="icon-check" class="mr-2"/> <span>{{item}}</span>
      </li>
    </ul>
    <div class="markdown" v-html="$md.render(body)"></div>
  </div>
</template>

<script>
import Icon from './../components/Icon'
export default {
  components: {
    Icon
  },
  data() {
    return {
      classic: [
        'Keine Leistungen',
      ]
    }
  },
  async asyncData(context) {
    const { route } = context
    const file = await require(`~/content/${route.name}.json`);
    return {
      ...file
    }
  }
}
</script>

<style>

</style>
