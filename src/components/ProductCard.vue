<script setup>
defineProps({
  product: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <div class="card" style="width: 18rem">
    <img
      :src="this.product.image + '?random' + Math.floor(Math.random() * 100)"
      class="card-img-top"
      :alt="this.product.name"
    />
    <div class="card-body">
      <h5 class="card-title">{{ this.product.name }}</h5>
    </div>
    <ul class="list-group list-group-flush">
      <li class="list-group-item">
        <i
          :class="{
            'fas fa-heart': this.product['added-to-wishlist'],
            'far fa-heart': !this.product['added-to-wishlist'],
          }"
        ></i>

        <i
          class="fas fa-dollar-sign"
          v-if="this.product.badges['collection-sale']"
        ></i>
        <i
          class="far fa-tachometer-slowest"
          v-if="this.product.badges['last-items']"
        ></i>
        <i class="fas fa-tag" v-if="this.product.badges.new"></i>
      </li>
      <li class="list-group-item">
        On stock: <strong> {{ this.product.amount }} items</strong>
      </li>
      <li class="list-group-item" v-if="this.product.price.current">
        Price
        <span style="text-decoration: line-through"
          >${{ this.product.price.regular / 100 }}</span
        >
        <strong> ${{ this.product.price.current / 100 }}</strong>
      </li>
      <li class="list-group-item" v-else>
        Price <strong>${{ this.product.price.regular / 100 }}</strong>
      </li>
      <li class="list-group-item">
        Rating
        <span v-for="n in this.product.rating" :key="n">
          <i class="fas fa-star"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.list-group-item i {
  margin-left: 10px;
}
</style>
<script>
export default {
  name: "ProductCard",

  computed: {
    url() {
      const random = this.product.image;
      return random;
    },
  },
};
</script>
