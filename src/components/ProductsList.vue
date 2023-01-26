<script setup>
import ProductDay from "./ProductCard.vue";
</script>

<template>
  <div class="row justify-content-center mt-5">
    <h2 class="text-center mb-3">Product of a day</h2>
    <div class="col-3">
      <ProductDay :product="this.productOfADay" />
    </div>
  </div>
  <div class="row justify-content-center mt-5">
    <h2 class="text-center mb-3">Best sales</h2>
    <div
      class="col-3 mt-3"
      v-for="(bestSale, index) in this.bestSales"
      :key="index"
    >
      <ProductDay :product="bestSale" />
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductList",

  data() {
    return {
      products: [],
      productOfADay: [],
      bestSales: [],
    };
  },
  created() {
    this.fetchProducts();
  },
  methods: {
    async fetchProducts() {
      const response = await fetch("http://localhost:8082/products", {
        method: "GET",
        mode: "cors",
        headers: {
          Accept: "*/*",
          "Content-Type": "application/json",
        },
      });
      const data = await response.json();
      this.productOfADay = data["product-of-a-day"];
      this.bestSales = data["best-sales"];
      this.products = data;
      console.log(this.products);
    },
  },
};
</script>
<style scoped></style>
