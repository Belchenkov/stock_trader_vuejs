<template>
    <div class="col-sm-6 col-md-4 mb-5">
      <div class="card">
        <div class="card-header bg-info">
          <h5 class="card-title text-white">
              {{ stock.name }}
              <small>(Price: {{ stock.price }} | Quantity: {{ stock.quantity }})</small>  
            </h5>
        </div>
        <div class="card-body d-flex justify-content-between">
            <div>
              <input 
                type="number"
                class="form-control"
                placeholder="Quantity"
                v-model="quantity"
                :class="{danger: insufficientQuantity}"
              >
            </div>
            <div>
              <button
                class="btn btn-success"
                @click="sellStock"
                :disabled="insufficientQuantity || quantity <= 0"
              >
                {{ insufficientQuantity ? 'Not enough' : 'Sell' }}
              </button>
            </div>
          </div>
      </div>
    </div>
</template>

<script>
  import { mapActions } from 'vuex';

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
      insufficientQuantity () {
        return this.quantity > this.stock.quantity;
      }
    },
    methods: {
     ...mapActions({
          placeSellOrder: 'sellStock'
     }), 
     sellStock () {
       const order = {
        stockId: this.stock.id,
        stockPrice: this.stock.price,
        quantity: this.quantity
       };
       this.placeSellOrder(order);
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
