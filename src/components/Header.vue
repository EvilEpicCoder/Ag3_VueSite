<template>
<div>
  <div> {{ geodata.code }} </div>
  <div> {{ geodata.city }} </div>
  <div> {{ geodata.country }} </div>
</div>
</template>

<script>
export default {
  component: 'Header',
  data () {
    return {
      title: 'EEC Portfolio',
      user: {
        firstname: 'Igor',
        lastname: 'Gavelyuk'
      },
      geodata: {
        code: 'code is unset',
        country: 'country is unset',
        city: 'city is unset'
      }
    }
  },
  methods: {
    is_working: function () {
      alert('is working ok')
    },
    test: () => alert('test ok'),
    ipApi: (superKey) => {
      var xhttp
      xhttp = new XMLHttpRequest()
      xhttp.onreadystatechange = function () {
        if (this.readyState === 4 && this.status === 200) {
          let tgeo = JSON.parse(this.responseText)
          superKey.code = tgeo.country_code
          superKey.country = tgeo.country_name
          superKey.city = tgeo.city
        }
      }
      xhttp.open('GET', 'https://freegeoip.net/json/', true)
      xhttp.send()
    }
  },
  beforeMount () {
    this.ipApi(this.geodata)
  }
}
</script>

<style>

</style>
