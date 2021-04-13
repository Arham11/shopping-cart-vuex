<template>
  <div class="Cart">
    <div v-if="!itemToBuy">You have no items in Cart</div>
    <div v-else>
      <h1 class="mb-4 font-bold">Your orders are Listed below</h1>
      <!-- <div>Total items : {{ TotalitemCount }}</div> -->
      <table class="w-full">
        <tr>
          <th class="whitespace-nowrap">Sr. No</th>
          <th>
            Image
          </th>
          <th>Title</th>

          <th>Category</th>
          <th>Quantity</th>
          <th>Price</th>
        </tr>
        <tr v-for="(item, index) in itemToBuy" :key="index">
          <td>{{ index + 1 }}</td>
          <td>
            <img :src="item.image" class="w-8 h-8" alt="" />
          </td>
          <td>{{ item.title }}</td>
          <td>{{ item.category }}</td>
          <th>{{ item.quantity }}</th>
          <td>$ {{ item.quantity * item.price }}</td>
        </tr>
        <tr>
          <td colspan="5" class="text-right font-bold">Total</td>
          <td>$ {{ totalPrice }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "Cart",
  computed: {
    itemToBuy() {
      return this.$store.state.cart;
    },
    totalPrice() {
      return this.$store.state.cart.reduce(
        (sum, i) => sum + i.price * i.quantity,
        0
      );
    },
  },
};
</script>

<style scoped>
td,
th {
  padding: 16px;
}
tr {
  border-bottom: 1px solid #eee;
}
</style>
