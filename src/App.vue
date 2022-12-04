<template>
  <div class="container">
    <h1 class="text-center">Product Add App</h1>
    <hr />
    <ProductAdd />
    <br /><br />
    <Progres />
    <br /><br />
    <Product/>
  </div>
</template>

<script>
import ProductAdd from './components/NewProduct.vue';
import Progres from './components/Progress.vue';
import Product from './components/Products.vue';
export default {
  components: {
    ProductAdd,
    Progres,
    Product
  },
 
}
</script>

<style>
body {
  background-color: aliceblue;
  padding-top: 20px;
  padding-bottom: 20px;
}

.card {
  margin-right: 5px;
  margin-bottom: 5px;
}

.card:last-child {
  margin-right: 0px;
}

.col-md-2 {
  max-width: 15.666667% !important;
}

.product-container {
  margin-left: 15px;
}
</style>

