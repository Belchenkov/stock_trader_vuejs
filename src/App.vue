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

<style scoped>
 .slide-enter-active {
   animation: slide-in 300ms ease-in forwards;
 }
 .slide-leave-active {
   animation: slide-out 300ms ease-in forwards;
 }

 @keyframes slide-in {
   from {
     transform: translateY(-30px);
     opacity: 0;
   }
   to {
     transform: translateY(0);
     opacity: 1;
   }
 }
 @keyframes slide-out {
   from {
     transform: translateY(0);
     opacity: 1;
   }
   to {
     transform: translateY(-30px);
     opacity: 0;
   }
 }
</style>
