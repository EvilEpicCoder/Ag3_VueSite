<template>
<div id="content">
  <div>
    <div> {{ weatherData.day }} , {{ weatherData.date }} </div>
    <div v-model="weatherData.tempH"> Максимальная температура (днем) {{ weatherData.tempH }} </div>
    <div> Минимальная температура (ночью) {{ weatherData.tempL }} </div>
  </div>
</div>
</template>

<script>
export default {
  props: [
    'geo',
    'weatherData'
  ],
  data () {
    return {
      content: 'content text'
    }
  },
  methods: {
    is_working: function () {
      alert('is working ok')
    },
    test: (resUlt) => alert(resUlt + ' test ok')

  }
}
</script>

<style>
#content {
  margin-top:100 px;
}
</style>
