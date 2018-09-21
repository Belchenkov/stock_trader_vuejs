<template>
  <div id="stocks" class="row">
    <app-stock v-for="stock in stocks" :stock="stock"></app-stock>
  </div>
</template>

<script>
import Stock from './Stock.vue'

export default {
  components: {
    appStock: Stock
  },
  data () {
    return {
    }
  },
  computed: {
    stocks () {
      return this.$store.getters.stocks;
    }
  }
}
</script>
