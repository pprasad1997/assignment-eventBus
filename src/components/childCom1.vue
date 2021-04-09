<template>
  <div>
    <table class="table table-bordered">
      <thead>
        <th>S.No</th>
        <th>Product Name</th>
        <th>Product Price</th>
        <th>Add</th>
      </thead>
      <tbody>
        <tr v-for="(product, id) in products" :key="id">
          <td>{{ product.id }}</td>
          <td>{{ product.name }}</td>
          <td>{{ product.price }}</td>
          <td @click="add(id)">Add</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import { eventBus } from "../eventBus.js";
console.log(eventBus);
export default {
  data() {
    return {
      products: [
        { id: 1, name: "apple", price: 100 },
        { id: 2, name: "mango", price: 30 },
        { id: 3, name: "orange", price: 25 },
        { id: 4, name: "banana", price: 20 },
        { id: 5, name: "pineapple", price: 40 },
        { id: 6, name: "papaya", price: 32 },
        { id: 7, name: "milk", price: 50 },
        { id: 8, name: "rice", price: 100 },
      ],
    };
  },
  methods: {
    add(id) {
      eventBus.$emit("cart", this.products[id]);
    },
  },
};
</script>

<style></style>
