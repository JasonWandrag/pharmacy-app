<template lang="html">
  <router-link
    class="product-card neu-border"
    :to="{ name: 'ProductDetails', params: { id: product.id } }"
  >
    <img class="neu-border-inset" :src="product.image" :alt="product.title" />
    <div class="product-card-details">
      <h3>{{ product.title }}</h3>
      <h4>R{{ product.price }}</h4>
    </div>
  </router-link>
</template>
<script>
export default {
  props: ["product"],
};
</script>
<style lang="scss">
.product-card {
  width: 31%;
  /* height: 100%; */
  display: inline-flex;
  align-items: center;
  padding: 10px;
  margin-bottom: 2%;
  color: #333;
  text-decoration: none;
  transition: all 0.1s linear;

  &:hover {
    transform: scale(1.05);
  }

  img {
    width: 100%;
    max-width: 100px;
    max-height: 100px;
    height: 100%;
    min-height: 100px;
    object-fit: cover;
    padding: 10px;
  }

  &-details {
    width: 100%;
    text-align: end;

    h3 {
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      max-width: 200px;
      margin-left: auto;
    }
  }
}

.neu-border {
  border-radius: 30px;
  background: #f5f5f5;
  box-shadow: 8px 8px 15px #e4e4e4, -8px -8px 15px #ffffff;

  &-inset {
    border-radius: 30px;
    background: #f5f5f5;
    box-shadow: inset 8px 8px 15px #e4e4e4, inset -8px -8px 15px #ffffff;
  }
}
</style>
