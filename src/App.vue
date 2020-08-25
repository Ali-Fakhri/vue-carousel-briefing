<template>
  <div>
    <h1 class="my-5 text-primary text-center">Carousel</h1>
    <VueCarousel :prods="products" />
    <hr />
    <ThreeDCarousel :prods="products" />
    <hr />
    <hr />
    <br />
    <h2 class="text-primary text-center">Slider - Ads & Promotions</h2>
    <AdsSlider />
  </div>
</template>

<script>
import axios from "axios";
import VueCarousel from "./components/VueCarousel";
import ThreeDCarousel from "./components/ThreeDCarousel";
import AdsSlider from "./components/AdsSlider";

export default {
  name: "App",
  data() {
    return {
      products: [],
    };
  },
  components: {
    VueCarousel,
    ThreeDCarousel,
    AdsSlider,
  },
  methods: {
    async fetchAndImport() {
      const response = await axios.get(
        "https://my-json-server.typicode.com/Ali-Fakhri/fakebe/products"
      );
      this.products = response.data;
    },
  },
  created() {
    this.fetchAndImport();
  },
};
</script>

<style></style>
