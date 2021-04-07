<template>
  <div class="product-card px-4 sm:w-1/2 mb-6">
    <div class="">
      <img
        :src="product.image"
        alt=""
        class="max-w-full max-h-full object-contain object-center inline-block h-40"
      />
    </div>
    <div class="text-base mb-4">
      {{ product.title }}
    </div>
    <div class="text-xs mb-2">{{ product.description }}</div>
    <div class="text-sm text-red-700">$ {{ product.price }}</div>
  </div>
</template>

<script>
export default {
  name: "ProductSummary",
  props: ["product"]
};
</script>