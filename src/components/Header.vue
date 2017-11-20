<template>
<div>
  <h1> Прогноз погоды в Vue</h1>
  <h2> Актуально на {{ weatherData.day }},{{ weatherData.date }}</h2>
  <h3> Вы находитесь в {{ geo.country }} , {{ geo.city }}</h3>
</div>
</template>

<script>
export default {
  props: [
    'geo',
    'weatherData'
  ],
  data  () {
    return {
      header: 'header'
    }
  },
  methods: {
    compute (val) {
      alert(val.country)
    }
  }
}
</script>

<style>

</style>
