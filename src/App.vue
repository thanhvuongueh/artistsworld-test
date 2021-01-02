<template>
  <div id="app">
    <Header></Header>
    <router-view/>
  </div>
</template>

<script>
import Header from '@/components/Header'

export default {
  components: {
    Header
  },
  name: 'App'
}
</script>

<style>
  @import './assets/app.css';
</style>
