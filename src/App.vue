<template>
  <div>
    <header>
      <button v-on:click="navigateTo('products')">View Products</button>
      {{cart.length}} in cart
      <button v-on:click="navigateTo('cart')">View Cart</button>
    </header>

    <div v-if="page === 'cart'">
      <h1> Carrito </h1>
      <div class="products">
        <div v-for="(product, index) in cart" :key="index">
        {{product.name}}
        <img :src="product.image">
        <div>{{product.cost}}</div>
        <button v-on:click="removeItemFromCart"> Quitar del carrito</button>
        </div>
      </div>
    </div>

    <div v-if="page === 'products'">
      <Products v-on:addItemToCart="addItemToCart"/>
    </div>
  </div>
  
</template>

<script>
import Products from './components/Products.vue'

export default{
  name: "App",
  data:() => {
    return{
      page: 'products',
      cart:[]
    };
  },
  methods :{
    addItemToCart(product){
      this.cart.push(product);
    },

    removeItemFromCart(product){
      this.cart.splice(this.cart.indexOf(product));
    },

    navigateTo(page){
      this.page = page;
    }
  },
  components :{
    Products
  }
};
</script>

<style>
.products{
  display:grid;
  grid-template-columns: 1fr 1fr;
}
</style>
