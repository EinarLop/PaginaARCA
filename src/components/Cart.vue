<!-- <template>
  <div>
    <h1>Tu Carrito</h1>
    <div class="products">
      <div v-for="(product, index) in cart" :key="index">
        <h3>{{ product.name }}</h3>
        <img :src="product.image" />
        <div>{{ product.cost }}</div>
        <button v-on:click="removeItemFromCart(product)">
          Quitar de carrito
        </button>
      </div>
    </div>
  </div>
</template> -->

<template>
  <div>
    <h1 class="ProductsTitle">Productos</h1>
    <div>
      <div class="ItemWrapper" v-for="(product, index) in cart" :key="index">
        <div class="Item">
          <h3 class="ItemTitle">{{ product.name }}</h3>
          <img class="ItemImg" :src="product.image" />
          <div class="ItemCost">{{ product.cost }}</div>

          <button v-on:click="removeItemFromCart(product)">
            Quitar de carrito
          </button>
        </div>
      </div>
    </div>
  </div>
  <div v-if="cart.length > 0" v-on:click="completePurchase()" class="PayButton">
    Completar compra
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: ["cart"],
  methods: {
    removeItemFromCart(product) {
      this.$emit("removeItemFromCart", product);
    },
    async completePurchase() {
      try {
        await axios.post(
          "https://https://547a-2601-647-5901-6cc0-2d63-b5ed-ad4-a9e2.ngrok.io/getItems",
          {
            id: window.location.href.split("=")[1],
            data: this.cart.map(({ image, ...keepAttrs }) => keepAttrs),
          }
        );
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style>
.products {
  display: grid;
  grid-template-columns: 1fr 1fr;
}

.PayButton {
  padding: 9px 25px;
  background-color: red;
  border: none;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease 0s;
  color: white;
  font-weight: 600;
  text-align: center;
  font-size: 18px;
  width: 75%;
  margin: 40px auto;
  min-width: 215px;
}
</style>
