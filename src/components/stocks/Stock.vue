<template>
    <div class="col-sm-6 col-md-4 mb-5">
      <div class="card">
        <div class="card-header bg-info">
          <h5 class="card-title text-white">
              {{ stock.name }}
              <small>(Price: {{ stock.price }})</small>  
            </h5>
        </div>
        <div class="card-body d-flex justify-content-between">
            <div>
              <input 
                type="number"
                class="form-control"
                placeholder="Quantity"
                v-model="quantity"
              >
            </div>
            <div>
              <button
                class="btn btn-success"
                @click="buyStock"
                :disabled="quantity <= 0"
              >Buy</button>
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

<style>
 
</style>
