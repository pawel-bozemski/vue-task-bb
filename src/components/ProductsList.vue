<script setup>
import ProductDay from "./ProductCard.vue";
</script>

<template>
  <div>
    <div class="row mt-5" id="prodofday" v-if="this.productOfADay.length !== 0">
      <h2 class="text-center mb-3">Product of a day</h2>
      <div class="col-3">
        <ProductDay :product="this.productOfADay" />
      </div>
    </div>
    <div class="row mt-5" id="bestsales" v-if="this.bestSales.length !== 0">
      <h2 class="text-center mb-3">Best sales</h2>
      <div
        class="col-3 mt-3"
        v-for="(bestSale, index) in this.bestSales"
        :key="index"
      >
        <ProductDay :product="bestSale" />
      </div>
    </div>
    <div
      class="row justify-content-center mt-5"
      id="recommended"
      v-if="this.recomended.length !== 0"
    >
      <h2 class="text-center mb-3">Recomended for you</h2>
      <div
        class="col-3 mt-3"
        v-for="(recommended, index) in this.recomended"
        :key="index"
      >
        <ProductDay :product="recommended" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductList",

  data() {
    return {
      productOfADay: [],
      bestSales: [],
      recomended: [],
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
      this.recomended = data["recommended-for-you"];
    },
  },
};
</script>
<style scoped></style>
