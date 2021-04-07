<template>
  <div class="home">
    <h1 class="mb-7 font-semibold text-lg">
      Amazing Product at your FingerTips
    </h1>
    <div class="flex flex-wrap">
      <ProductSummary
        v-for="product in items"
        :key="product"
        :product="product"
      />
    </div>
  </div>
</template>

<script>
import ProductSummary from "../components/products/productSummaryCard";
import items from "../data/index.js";

export default {
  name: "Home",
  components: {
    ProductSummary
  },
  setup() {
    return {
      items
    };
  }
};
</script>


