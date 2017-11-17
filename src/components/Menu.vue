<template>
<div>

<button v-for="all in name" :key="all.key" v-on:click="test(valid[all])">{{all}}</button>
</div>
</template>

<script>
export default {
  component: 'Menu',
  data () {
    return {
      name: [
        'Menu',
        'Меню'
      ],
      valid: {
        Menu: 'en',
        Меню: 'ru'
      }
    }
  },
  methods: {
    is_working: function () {
      alert('is working ok')
    },
    test: (el) => alert(el + ' test ok')

  }
}
</script>

<style>

</style>
