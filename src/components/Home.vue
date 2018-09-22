<template>
  <div class="jumbotron">
    <h1 class="display-4">Trade or View your Portfolio</h1>
    <h6 class="lead my-3">You may Save & Load your Data</h6>
    <p>Click on 'End Day' to begin a New Day!</p>
    <hr class="my-4">
    <p class="lead">
      Your Funds: {{ funds }}
    </p>
</div>
</template>

<script>
  export default {
    computed: {
      funds () {
        return this.$store.getters.funds;
      }
    }  
  }
</script>
