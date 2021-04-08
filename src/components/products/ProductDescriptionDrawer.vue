<template>
  <div class="product-drawer fixed top-0 bottom-0 p-4 bg-white">
    <div class="text-right mb-4">
      <span
        class="bg-gray-300 leading-none rounded-full px-2 py-1 text-white justify-items-end cursor-pointer"
        @click="close"
        >x</span
      >
    </div>
    <div>
      {{ product.description }}
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductDescriptionDrawer",
  props: {
    product: {
      default: ""
    }
  },
  setup(props, { emit }) {
    function close() {
      emit("close");
    }
    return {
      close
    };
  }
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