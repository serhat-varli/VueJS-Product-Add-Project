<template>
  <div class="row">
    <div class="card offset-2 col-md-3">
      <div class="card-body tex-center d-flex align-items-center flex-column">
        <img height="128" class="img-responsive text-center mb-3"
          :src="product.selectedImage == null ? '/src/assets/default.png' : product.selectedImage">
        <input ref="file" type="file" style="display: none;" @change="onChange($event)" class="form-control">
        <button class="btn btn-outline-secondary " type="button" @click="$refs.file.click()">İmage Select</button>
      </div>
    </div>
    <div class="col-md-5">
      <div class="col-md-11 card">
        <div class="card-body">
          <div class="form-group">
            <label>Product Name</label>
            <input type="text" v-model="product.title" class="form-control" placeholder="name enter">
          </div>
          <div class="row">
            <div class="form-group col-md-6">
              <label>Product Count</label>
              <input type="text" v-model="product.count" class="form-control" placeholder="count enter">
            </div>
            <div class="form-group col-md-6">
              <label>Product Price</label>
              <input type="text" v-model="product.price" class="form-control" placeholder="price enter">
            </div>
          </div>
          <button class="btn btn-outline-info btn-block" @click="productAdd">Add!</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from '../main';

export default {
  data() {
    return {
      imageList: [],
      product: {
        title: null,
        count: null,
        price: null,
        totalPrice: null,
        selectedImage: null
      }
    }
  },
  methods: {
    onChange(e) {
      const file = e.target.files[0];
      this.product.selectedImage = URL.createObjectURL(file);
    },
    productAdd() {
      this.product.totalPrice = this.product.count * this.product.price
      eventBus.$emit("productAdded", this.product);
      this.product = {
        title: null,
        count: null,
        price: null,
        totalPrice: null,
        selectedImage: null
      }
    }
  }
}
</script>