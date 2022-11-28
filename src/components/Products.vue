<template>
  <div>
    <h1 class="ProductsTitle">Productos</h1>
    <div>
      <div
        class="ItemWrapper"
        v-for="(product, index) in products"
        :key="index"
      >
        <div class="Item">
          <h3 class="ItemTitle">{{ product.name }}</h3>
          <img class="ItemImg" :src="product.image" />
          <div class="ItemCost">{{ product.cost }}</div>

          <button v-on:click="addItemToCart(product)">
            Agregar al carrito
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      products: [
        {
          name: "Agua Ciel Exprim Pina Jengibre 1L",
          cost: "$78.00",
          image:
            "https://www.coca-colaentuhogar.com/media/catalog/product/c/i/ciel_xprim_vis2018_pi_a_jengibre_pet1ml_seco_1_optimized_4.jpg?optimize=medium&fit=bounds&height=175&width=175&canvas=175:175",
        },
        {
          name: "Agua Ciel Exprim Fresa 1L",
          cost: "$14.00",
          image:
            "https://www.coca-colaentuhogar.com/media/catalog/product/3/9/39_ciel-exprim-fresa-1-l-botella-pet_5_1.jpg?optimize=medium&fit=bounds&height=175&width=175&canvas=175:175",
        },
        {
          name: "Agua Ciel Exprim Jamaica 1.5L",
          cost: "$95.00",
          image:
            "https://www.coca-colaentuhogar.com/media/catalog/product/4/5/45_ciel-exprim-jamaica-reposada-1.5-l-botella-pet_5.jpg?optimize=medium&fit=bounds&height=175&width=175&canvas=175:175",
        },
      ],
    };
  },
  methods: {
    addItemToCart(product) {
      this.$emit("addItemToCart", product);
    },
  },
};
</script>

<style>
.ProductsTitle {
  text-align: center;
}
.ItemWrapper {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.Item {
  margin-top: 25px;
  width: 100%;
  max-width: 320px;
  background-color: white;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

.ItemTitle {
  text-align: center;
  width: 100%;
}

.ItemCost {
  width: 100%;
  text-align: center;
  margin-bottom: 10px;
}
</style>
