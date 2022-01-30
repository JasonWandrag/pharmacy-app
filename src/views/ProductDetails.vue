<template>
  <div v-if="product">
    <div class="product">
      <img
        class="product-image neu-border"
        :src="product.image"
        :alt="product.title"
      />
      <div class="product-details">
        <h2>{{ product.title }}</h2>
        <h4>{{ product.category }}</h4>
        <p>{{ product.description }}</p>
        <p>R{{ product.price }}</p>
      </div>
    </div>
    <hr style="margin: 30px" />
    <h3>Related Products</h3>
    <div class="products-container">
      <ProductCard
        v-for="product of similarProducts"
        :key="product.id"
        :product="product"
      />
    </div>
  </div>
  <div v-else>Loading the product...</div>
</template>
<script>
import ProductCard from "@/components/products/ProductCard.vue";

export default {
  components: { ProductCard },
  props: ["id"],
  data() {
    return {
      product: null,
      similarProducts: null,
    };
  },
  mounted() {
    fetch("https://fakestoreapi.com/products/" + this.id)
      .then((res) => res.json())
      .then((data) => {
        this.product = data;
        return fetch(
          "https://fakestoreapi.com/products/category/" + data.category
        );
      })
      .then((res) => res.json())
      .then((data) => (this.similarProducts = data));
  },
};
</script>
<style>
.product {
  display: flex;
  padding: 0 10%;
  /* max-width: 600px; */
  margin-inline: auto;
  align-items: stretch;
  gap: 30px;
}
.product-image {
  padding: 10px;
  width: 50%;
  max-height: 80vh;
  object-fit: contain;
}
.product-details {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: center;
  text-align: end;
  gap: 8px;
}

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
.neu-border {
  border-radius: 30px;
  background: #f5f5f5;
  box-shadow: 8px 8px 15px #e4e4e4, -8px -8px 15px #ffffff;
}
.neu-border-inset {
  border-radius: 30px;
  background: #f5f5f5;
  box-shadow: inset 8px 8px 15px #e4e4e4, inset -8px -8px 15px #ffffff;
}
</style>
