<template>
  <div class="product-drawer fixed inset-0 p-4 bg-white">
    <div class="w-1/2 mx-auto">
      <div class="text-right mb-4 -mx-10">
        <span
          class="bg-gray-300 leading-none rounded-full px-2 py-1 text-white justify-items-end cursor-pointer"
          @click="close"
          >x</span
        >
      </div>
      <div class="text-lg mb-4 font-bold">
        {{ product.title }}
      </div>
      <div class="mb-4 text-base">
        {{ product.description }}
      </div>
      <div class="mb-5">
        <span>Price : </span>
        <span class="text-red-700">$ {{ product.price }}</span>
      </div>
      <div v-if="product_total">
        <h3>In cart</h3>
        <div class="text-base mb-4 font-semibold">
          {{ product_total }}
        </div>
      </div>

      <div>
        <button
          @click="removeFromCart"
          class="bg-gray-400 py-1 w-32 text-white font-bold rounded-md px-7 ml-3 inline-block"
        >
          Remove
        </button>
        <button
          @click="addToCart"
          class="bg-gray-400 py-1 w-32 text-white font-bold rounded-md px-7 mr-3 inline-block"
        >
          Add
        </button>
      </div>
      <!-- <div
        @click="addToCart(product)"
        class="md:w-1/2 mx-auto bg-green-500 py-3 px-2 text-white font-bold rounded-md px-7 mt-4 cursor-pointer"
      >
        Add To Cart
      </div> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductDescriptionDrawer",
  props: {
    product: {
      default: "",
    },
  },
  setup(props, { emit }) {
    function close() {
      emit("close");
    }
    return {
      close,
    };
  },
  methods: {
    addToCart() {
      this.$store.commit("addToCart", this.product);
    },
    removeFromCart() {
      this.$store.commit("removeFromCart", this.product);
    },
  },
  computed: {
    product_total() {
      return this.$store.getters.productQuantity(this.product);
    },
  },
};
</script>

<style lang="scss" scoped>
// .product-drawer {
//   background-color: #fff;
//   &:after {
//     content: "";
//     position: fixed;
//     top: 0;
//     bottom: 0;
//     height: 100%;
//     width: 100%;
//     left: 0;
//     right: 0;
//     background-color: rgba(0, 0, 0, 0.5);
//   }
// }
</style>
