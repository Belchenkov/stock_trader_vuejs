<template>
  <div id="navbar">
    <nav class="navbar navbar-expand-lg navbar-dark bg-info">
      <router-link to="/" class="navbar-brand">
        <img src="data:image/png;base64,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">
        Stock Trader
      </router-link>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarColor02" aria-controls="navbarColor02" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

    <div class="collapse navbar-collapse" id="navbarColor02">
      <ul class="navbar-nav mr-auto">
          <router-link 
            to="/portfolio" 
            class="nav-item" 
            activeClass="active"
            tag="li"
          >
            <a class="nav-link">
              <i class="fas fa-book"></i> Portfolio
            </a>
          </router-link>
          <router-link 
            to="/stocks" 
            class="nav-item" 
            activeClass="active"
            tag="li"
          >
            <a class="nav-link">
              <i class="fas fa-file-invoice-dollar"></i> Stocks
            </a>
          </router-link>
      </ul>
      <ul class="nav navbar-nav navbar-right">
         <li class="nav-item">
            <a class="nav-link" href="#" @click="endDay">
              <i class="fas fa-hourglass-end"></i> End Day
            </a>
        </li>
        <li>
          <a 
            class="nav-link dropdown-toggle" 
            href="#" 
            id="navbarDropdown" 
            role="button" 
            data-toggle="dropdown" 
            aria-haspopup="true" aria-expanded="false"
          ><i class="far fa-save"></i> 
            Save & Load
          </a>
          <div class="dropdown-menu" aria-labelledby="navbarDropdown">
            <a class="dropdown-item" href="#">Save Data</a>
            <a class="dropdown-item" href="#">Load Data</a>
          </div>
      </li>
      </ul>
      <strong class="navbar-text navbar-right">
         Funds: {{ funds | currency }}</strong>
    </div>
  </nav>
  </div>
</template>

<script>
  import { mapActions } from 'vuex'

  export default {
    computed: {
      funds () {
        return this.$store.getters.funds;
      }
    },
    methods: {
      ...mapActions([
        'randomizeStocks'
      ]),
      endDay () {
          this.randomizeStocks();
      }
    }
  }
</script>

<style>
 @import url('https://fonts.googleapis.com/css?family=Rajdhani|Righteous');
  
  .navbar-brand {
    font-family: 'Righteous', cursive;
    text-shadow: 0 0 3px black;
  }

  .nav-link {
    font-family: 'Rajdhani', sans-serif;
    text-shadow: 0 0 3px black;
  }
</style>
