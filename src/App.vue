<template>
  <div>
    
    <header>
      <img class="logo" src="https://www.coca-colaentuhogar.com/static/version1666879807/frontend/FortyFour/mx-cceth/es_MX/images/logo-cceth-stack.svg">
      <nav>
        <ul class="nav_links">
          <li><a v-on:click="navigateTo('products')">Productos</a></li>
          <li><a v-on:click="navigateTo('cart')">Mi Carrito</a></li>
        </ul>
      </nav>
      
      {{cart.length}} en tu carrito
      
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
body{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  
}

li, a, button{
  font-family: 'TCCC-UnityText','Helvetica Neue',Helvetica,Arial,sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  color: #edf0f1;
}

header{
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 30px 10%;
}

.logo{
  cursor: pointer;
}

.nav_links{
  list-style: none;
}

.nav_links li{
  display: inline-block;
  padding: 0px 20px;
}

.nav_links li a{
  transition: all 0.3s ease 0s;
}

.nav_links li a:hover{
  color: #0088a9;
}

button{
  padding: 9px 25px;
  background-color: rgba(0,136,169,1);
  border: none;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease 0s;
}

button:hover{
  background-color: rgba(0,136,169,0.8);
}

.logo{
  height: 50px;
}
/* body {
    color: #333;
    
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
} */
</style>