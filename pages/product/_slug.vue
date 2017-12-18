<template>
  <div class="product full-view padding-lg padding-v">
    <div class="container--row">
      <SwProduct full-view="true"></SwProduct>
    </div>
  </div>
</template>

<script>
  import SwProduct from '~/components/Product.vue'

  export default {
    components: {
      SwProduct
    },
    fetch ({ store, params }) {
      console.log('params', params)
    }
  }
</script>

<style></style>
