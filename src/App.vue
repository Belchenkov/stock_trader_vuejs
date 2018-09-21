<template>
  <div class="app">
    <app-header></app-header>
     <div class="container pt-3">
    <router-view></router-view>
  </div>
</div>
</template>

<script>
import Header from './components/Header.vue'
export default {
  name: 'App',
  components: {
    appHeader: Header
  },
  created () {
    this.$store.dispatch('initStocks');
  }
}
</script>

<style>
 
</style>
