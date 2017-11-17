<template>
<div> {{ name }} </div>
</template>

<script>
export default {
  component: 'Menu',
  data () {
    return {
      name: 'Navbar'
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
