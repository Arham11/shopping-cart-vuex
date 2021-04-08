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
        @veiwDetails="onveiwDetails"
      />
    </div>
    <ProductDescriptionDrawer
      :product="viewDetailsParams"
      v-if="showDrawer"
      @close="onClose"
    />
    {{ showDrawer }}
  </div>
</template>

<script>
import ProductSummary from "../components/products/productSummaryCard";
import ProductDescriptionDrawer from "../components/products/ProductDescriptionDrawer";
import items from "../data/index.js";
import { ref } from "vue";

export default {
  name: "Home",
  components: {
    ProductSummary,
    ProductDescriptionDrawer
  },
  setup() {
    let viewDetailsParams = ref({});
    var showDrawer = ref(false);

    console.log(showDrawer.value);

    function onveiwDetails(e) {
      viewDetailsParams.value = e;
      showDrawer.value = true;
      console.log(showDrawer.value);
      //const el = document.body;
      //el.classList.add("overflow-hidden", "bg-gray-500", "third");
    }

    function onClose() {
      showDrawer.value = false;
    }

    return {
      items,
      onveiwDetails,
      viewDetailsParams,
      showDrawer,
      onClose
    };
  }
};
</script>


