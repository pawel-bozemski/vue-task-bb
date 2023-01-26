<script setup>
import ProductsList from "./components/ProductsList.vue";
import NavBar from "./components/NavBar.vue";
</script>

<template>
  <div class="container" id="top">
    <header>
      <NavBar />
    </header>
    <ProductsList />
  </div>
  <footer>
    <NavBar />
  </footer>
</template>

<style scoped></style>
