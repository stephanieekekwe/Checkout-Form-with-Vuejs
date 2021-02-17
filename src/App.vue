<template>
  <div class="container mt-5">
    <header class="text-center mb-5">
      <h2 class="pt-4">CHECKOUT FORM</h2>
    </header>
    <div class="row">
      <div class="col-md-4 order-md-2 mb-4">
        <ProductList />
      </div>
      <div class="col-md-8 order-md-1">
        <CheckoutForm />
      </div>
    </div>
  </div>
</template>

<script>
import CheckoutForm from "./components/CheckoutForm.vue";
import ProductList from "./components/ProductList.vue";

export default {
  name: "App",
  components: {
    CheckoutForm,
    ProductList,
  },
};
</script>

<style>
* {
  font-family: "sans-serif";
}
</style>
