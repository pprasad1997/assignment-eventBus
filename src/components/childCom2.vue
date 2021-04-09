<template>
  <div>
    <p>Cart</p>
    <table class="table table-bordered">
      <thead>
        <th>S.No</th>
        <th>Product Name</th>
        <th>Product Price</th>
        <th>Remove</th>
      </thead>
      <tbody>
        <tr v-if="!data">
          <td colspan="4">No Data available</td>
        </tr>
        <tr v-for="(product, id) in products" :key="id">
          <td>{{ product.id }}</td>
          <td>{{ product.name }}</td>
          <td>{{ product.price }}</td>
          <td @click="remove(id)">Remove</td>
        </tr>
      </tbody>
    </table>
    <div>
      <h3>Total = {{ total }}</h3>
    </div>
  </div>
</template>

<script>
import { eventBus } from '../eventBus.js'
export default {
  data(){
    return{
      data: false,
      products: [],
      total : 0
    }
  },
  mounted(){
    eventBus.$on('cart', (data) => {
      // this.price += data;
      this.data = true;
      this.products.push(data);
      this.total += data.price
    })
  },
  methods: {
    remove(id){
      this.total -= this.products[id].price;
      this.products.splice(id, 1);
      if(this.products.length == 0){
        this.data = false;
      }
    }
  }
}
</script>

<style>

</style>