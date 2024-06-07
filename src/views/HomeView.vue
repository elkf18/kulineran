<template>
  <div class="home">
    <NavbarSite />
    <div class="container">
      <HeroC />
      <div class="row mt-4">
        <div class="col">
          <h2>Best <strong>Foods</strong></h2>
        </div>
        <div class="col">
          <router-link to="/foods" class="btn btn-success float-right"
            ><b-icon-eye></b-icon-eye>Lihat semua</router-link
          >
        </div>
      </div>
      <div class="row mb-4">
        <div class="col-md-4 mt-4" v-for="product in products" :key="product.id">
          <CardProduct :product="product"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import NavbarSite from "@/components/NavbarSite.vue";
import HeroC from "@/components/HeroC.vue";
import CardProduct from "@/components/CardProduct.vue";
import axios from "axios";

export default {
  name: "HomeView",
  components: {
    NavbarSite,
    HeroC,
    CardProduct,
  },
  data() {
    return {
      products: [],
    };
  },
  methods: {
    setProducts(data) {
      this.products = data;
    },
  },
  mounted() {
    axios
      .get("http://localhost:3000/best-products")
      .then((response) =>
        this.setProducts(response.data)
        // handle success
        // console.log("Berhasil: ", response);
      )
      .catch((error) =>console.log(error));
  },
};
</script>
