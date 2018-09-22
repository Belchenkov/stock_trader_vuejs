<template>
    <div class="col-sm-6 col-md-4 mb-5">
      <div class="card">
        <div class="card-header bg-info">
          <h5 class="card-title text-white">
              {{ stock.name }}
              <small>(Price: {{ stock.price | currency}})</small>  
            </h5>
        </div>
        <div class="card-body d-flex justify-content-between">
            <div>
              <input 
                type="number"
                class="form-control"
                placeholder="Quantity"
                v-model="quantity"
                :class="{danger: insufficientFunds}"
              >
            </div>
            <div>
              <button
                class="btn btn-success"
                @click="buyStock"
                :disabled="insufficientFunds || quantity <= 0"
              >
              {{ insufficientFunds ? 'Insufficient Funds' : 'Buy' }}
              </button>
            </div>
          </div>
      </div>
    </div>
</template>

<script>
  export default {
    props: [
      'stock'
    ],
    data () {
      return {
        quantity: 0
      }
    },
    computed: {
      funds () {
        return this.$store.getters.funds;
      },
      insufficientFunds () {
        return this.quantity * this.stock.price > this.funds;
      }
    },
    methods: {
      buyStock () {
        const order = {
          stockId: this.stock.id,
          stockPrice: this.stock.price,
          quantity: this.quantity
        };
        this.$store.dispatch('buyStock', order);
        this.quantity = 0;
      }
    }
  }
</script>

<style scoped>
  .danger {
    border: 1px solid red;
  }
</style>
