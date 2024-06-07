<template>
  <div class="food-detail">
    <NavbarSite />
    <div class="container">

    <!-- Breadcrumb -->
      <div class="row mt-5">
        <div class="col">
          <nav aria-label="breadcrumb">
            <ol class="breadcrumb">
              <li class="breadcrumb-item">
                <router-link to="/" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item">
                <router-link to="/foods" class="text-dark">Home</router-link>
              </li>
              <li class="breadcrumb-item active" aria-current="page">
                Food Order
              </li>
            </ol>
          </nav>
        </div>
      </div>
      <!-- Food Detail -->
      <div class="row">
        <div class="col-md-6">
            <img :src=" 'assets/images/' + product.gambar " class="img-fluid shadow" />
        </div>
        <div class="col">
            <h2><strong>{{ product.nama }}</strong></h2>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import NavbarSite from "@/components/NavbarSite.vue";
import axios from "axios";
export default {
  name: "FoodDetail",
  components: {
    NavbarSite,
  },
  data() {
    return {
      product: {},
     
    };
  },
  methods: {
    setProduct(data) {
      this.product = data;
    },

  },

  mounted() {
    axios
      .get("http://localhost:3000/products/" + this.$route.params.id)
      .then((response) => this.setProduct(response.data))
      .catch((error) => console.log(error));
  },
};
</script>

<style></style>
