<template>
  <div class="home">
    <div class="container" id="products-display">
      <br />
      <h1>{{ message }}</h1>
      <hr />
      <div class="row">
        <div class="col-sm-4" v-for="product in products" v-bind:src="product.id">
          <div class="card">

            <img v-bind:src="product.images[0] && product.images[0].url" class="card-img-top" alt="no image found">

            <div class="card-body">
              <h5 class="card-title">{{ product.name }}</h5>
              <p>${{ product.price }}</p>
              <a href="#" class="btn btn-primary">Add to Cart</a>
            </div>
          </div>
          <br />
        </div>
      </div>
    </div>
  </div>
</template>

<style>
h1 {
  font-weight: bold;
}

.card {
  margin: 4px;
  background-color: #c5d7bd;
  border-width: 2px;
  border-color: #383e56;
}

.btn-primary {
  background-color: #fb743e;
  border-width: 1px;
  border-color: #383e56
}

.btn-primary:hover {
  background-color: #ff986f;
}

.card-img-top {
  border-bottom: 1px solid;
  border-color: #383e56;
  border-radius: 0px;
}

#products-display {
  background-color: #9fb8ad;
  border-radius: 10px;
}
</style>

<script>
import axios from "axios";

export default {
  data: function() {
    return {
      message: "Products",
      products: [],
      errors: [],
    };
  },
  created: function() {
    this.productsIndex();
  },
  methods: {
    productsIndex: function () {
      axios.get("http://localhost:3000/api/products")
        .then(response => {
          this.products = response.data;
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        });
    }
  }
};
</script>