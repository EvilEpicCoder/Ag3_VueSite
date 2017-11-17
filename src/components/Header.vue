<template>
<div> {{ title }} </div>
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
      }
    }
  },
  methods: {
    is_working: function () {
      alert('is working ok')
    },
    test: () => alert('test ok')
  }
}
</script>

<style>

</style>
