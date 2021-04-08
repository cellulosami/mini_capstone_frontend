<template>
  <div class="home">
    <br />
    <h1>{{ message }}</h1>
    <hr />
    <h5>{{ currentProduct.name }}</h5>
    <p>{{ currentProduct.description }}</p>
    <br />
    <button id="back-button">
      <router-link to="/products" id="back-button-text">
        Back to Products
      </router-link>
    </button>
  </div>
</template>

<style>
#back-button {
  border-radius: 5px;
  margin-bottom: 10px;
  background-color: rgb(226, 226, 226);
}

#back-button-text {
  text-decoration: none;
  color: #383e56;
}
</style>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      message: "Show",
      currentProduct: {},
      errors: []
    };
  },
  created: function() {
    this.productsShow();
  },
  methods: {
    productsShow: function () {
      console.log("showing...");
      axios
        .get("/api/products/" + this.$route.params.id)
        .then(response => {
          this.currentProduct = response.data;
        })
        .catch(error => {
          this.errors = error.response.data.errors;
        })
    }
  }
};
</script>