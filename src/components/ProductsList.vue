<script setup>
import ProductDay from "./ProductDay.vue";
</script>

<template>
  <div class="row justify-content-center mt-5">
    <div class="col-4">
      <ProductDay />
    </div>
  </div>
  <div></div>
</template>

<script>
export default {
  name: "ProductList",

  data() {
    return {
      products: [],
    };
  },
  mounted() {
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
      this.products = data;
    },
  },
};
</script>
<style scoped></style>
