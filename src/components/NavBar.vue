<script setup></script>

<template>
  <ul class="nav justify-content-center pt-3 pb-3">
    <li class="nav-item">
      <a class="nav-link" @click="this.scrollToOnClick('top')">Home</a>
    </li>
    <li class="nav-item">
      <a class="nav-link" @click="this.scrollToOnClick('prodofday')"
        >Product of a Day</a
      >
    </li>
    <li class="nav-item" @click="this.scrollToOnClick('bestsales')">
      <a class="nav-link">Best Sales</a>
    </li>
    <li class="nav-item" @click="this.scrollToOnClick('recommended')">
      <a class="nav-link">Recomended</a>
    </li>
  </ul>
</template>

<style scoped></style>
<script>
export default {
  methods: {
    scrollToOnClick(element) {
      const el = document.getElementById(element);
      el.scrollIntoView({ behavior: "smooth" });
    },
  },
};
</script>
