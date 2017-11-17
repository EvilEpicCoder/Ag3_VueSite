<template>
<div> {{ title }} </div>
</template>

<script>
export default {
  component: 'Footer',
  data () {
    return {
      title: 'Copyright 2017'
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
