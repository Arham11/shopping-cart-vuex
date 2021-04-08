<template>
  <div class="product-card p-4 sm:w-1/2 w-full md:w-1/3 border-gray-200">
    <div class="mb-4">
      <img
        :src="product.image"
        alt=""
        class="max-w-full max-h-full object-contain object-center inline-block h-40"
      />
    </div>
    <div class="text-base mb-4 truncate">
      {{ product.title }}
    </div>
    <!-- <div class="text-xs mb-2">{{ product.description }}</div> -->
    <div class="flex justify-around items-center text-sm ">
      <div>
        <span>Price : </span>
        <span class="text-red-700">$ {{ product.price }}</span>
      </div>
      <button
        @click="veiwDetails"
        class="bg-green-500 p-2 text-white font-bold rounded-md focus:bg-green-600"
      >
        View Details
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductSummary",
  props: ["product"],
  emits: ["veiwDetails"],
  setup(props, { emit }) {
    function veiwDetails() {
      emit("veiwDetails", props.product);
    }
    return {
      veiwDetails
    };
  }
};
</script>

<style lang="scss" scoped>
.sm\:max-w-1\/2 {
  max-width: 50%;
}
</style>