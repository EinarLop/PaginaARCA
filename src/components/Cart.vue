<template>
    <div>
      <h1>Tu Carrito</h1>
      <div class="products">
        <div v-for="(product, index) in cart" :key="index">
          <h3>{{product.name}}</h3>
          <img :src="product.image" />
          <div>{{product.cost}}</div>
          <button v-on:click="removeItemFromCart(product)">Remove from cart</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ["cart"],
    methods: {
      removeItemFromCart(product) {
        this.$emit("removeItemFromCart", product);
      }
    }
  };
  </script>
  
<style>
.products{
  display:grid;
  grid-template-columns: 1fr 1fr;
}
</style>