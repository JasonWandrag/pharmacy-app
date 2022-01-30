<template>
  <div v-if="products">
    <h2>Products</h2>
    <div class="products-container">
      <ProductCard
        v-for="product of products"
        :key="product.id"
        :product="product"
      />
    </div>
  </div>
  <div v-else>Loading products...</div>
</template>
<script>
import ProductCard from "@/components/products/ProductCard.vue";

export default {
  components: { ProductCard },
  data() {
    return {
      products: null,
    };
  },
  mounted() {
    fetch("https://fakestoreapi.com/products")
      .then((res) => res.json())
      .then((data) => (this.products = data));
  },
};
</script>
<style>
.products-container {
  display: flex;
  flex-wrap: wrap;
  /* max-width: 600px; */
  width: 100%;
  margin-inline: auto;
  padding: 30px;
  /* overflow: auto; */
  gap: 2%;
  justify-content: stretch;
  align-items: stretch;
}
</style>
