<template>
  <div>
    <a class="logo" href="https://www.coca-colaentuhogar.com/" title="Coca-Cola en tu Hogar" aria-label="store logo"><picture><source srcset="https://www.coca-colaentuhogar.com/static/version1666879807/frontend/FortyFour/mx-cceth/es_MX/images/logo.svg" media="(max-width: 767px)"><source srcset="https://www.coca-colaentuhogar.com/static/version1666879807/frontend/FortyFour/mx-cceth/es_MX/images/logo-cceth-stack.svg" media="(max-width: 1024px)"><img src="https://www.coca-colaentuhogar.com/static/version1666879807/frontend/FortyFour/mx-cceth/es_MX/images/logo.svg" title="Coca-Cola en tu Hogar" alt="Coca-Cola en tu Hogar" width="270" height="40"></picture></a>
    
    <header>
      <button v-on:click="navigateTo('products')">Productos</button>
      {{cart.length}} in cart
      <button v-on:click="navigateTo('cart')">Carrito</button>
    </header>

    <div v-if="page === 'cart'">
      <Cart v-on:removeItemFromCart="removeItemFromCart" :cart="cart" />
    </div>

    <div v-if="page === 'products'">
      <Products v-on:addItemToCart="addItemToCart" />
    </div>
  </div>
</template>

<script>
import Products from "./components/Products.vue";
import Cart from "./components/Cart.vue";
export default {
  name: "App",
  data: () => {
    return {
      page: "products",
      cart: []
    };
  },
  methods: {
    addItemToCart(product) {
      this.cart.push(product);
    },
    removeItemFromCart(product) {
      this.cart.splice(this.cart.indexOf(product), 1);
    },
    navigateTo(page) {
      this.page = page;
    }
  },
  components: { Products, Cart }
};
</script>

<style>
body {
  color: #333;
    font-family: 'TCCC-UnityText','Helvetica Neue',Helvetica,Arial,sans-serif;
    font-style: normal;
    font-weight: 400;
    line-height: 1.42857143;
    font-size: 1.4rem;
}
.products {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
.products button {
  padding: 10px;
  background-color: black;
  color: white;
  outline: none;
  border: none;
  cursor: pointer;
}
</style>

<style>
  .products{
  display:grid;
  grid-template-columns: 1fr 1fr;
}
body{
  margin: 0;
}
header{
  height: 100px;
  text-align: right;
}
</style>