<template>
<div> {{ title }} </div>
</template>

<script>
export default {
  component: 'Content',
  data () {
    return {
      title: 'General inforation'
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
