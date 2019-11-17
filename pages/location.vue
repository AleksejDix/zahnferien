<template>
  <div>
    <h1 class="title"> {{title}}</h1>
    <hr class="border-t-4 border-blue-500 rounded my-6">
    <div class="markdown">

      <img class="" :src="`https://image.maps.api.here.com/mia/1.6/mapview?app_id=Yxo5Jaup3FK4OcKI1dVN&app_code=wF15NPNC1c2Q1GvYHIUU4g&co=Switzerland&z=13&ci=Dubendorf&s=Sonnentalstr&n=10&h=720&w=1280&u=200`" alt="karte zahnurlaub.com"/>

      <h2>Adresse</h2>
      <div class="">
        <div class="mb-2">
          <div class="text-black font-bold leading-tight">Zahnurlaub</div>
          <div class="text-black text-gray-700 leading-tight mb-2">Lidia Dix</div>
          <div class="text-gray-700 leading-tight">Sonnentalstrasse 10</div>
          <div class="text-gray-700 leading-tight">8600 Dübendorf</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData(context) {
    const { route } = context
    const file = await require(`~/content/${route.name}.json`);
    return {
      ...file
    }
  },
  async mounted() {
    const response = fetch('https://image.maps.api.here.com/mia/1.6/mapview?app_id=Yxo5Jaup3FK4OcKI1dVN&app_code=wF15NPNC1c2Q1GvYHIUU4g&c=9.2515759,51.9875304&u=2k&h=300&w=420')
  }
}
</script>
