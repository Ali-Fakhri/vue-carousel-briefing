<template>
  <div class="container-fluid">
    <div class="py-3 row bg-gray">
      <h4 class="text-success mt-0 mb-3">Air Conditioners: (3D-Carousel)</h4>
      <div class="col-sm-10 offset-sm-1 py-3 bg-white">
        <!-- Something to Render incase Products Didn't Fetched (Error Boundary) -->
        <template v-if="!prods.length">
          <p>Loading</p>
        </template>
        <!-- Render List and it's Products   -->
        <template v-else>
          <carousel-3d
            :controls-visible="true"
            :clickable="false"
            :autoplay="true"
            :display="10"
            :autoplay-timeout="3000"
            :width="200"
            :height="600"
            :autoplayHoverPause="true"
          >
            <slide
              v-for="(prod, index) in prods"
              :key="index"
              :index="index"
              style="min-width: 300px"
            >
              <div class="card mx-2 p-3">
                <i class="far fa-heart text-right cursor"></i>
                <img
                  :src="prod.imgSrc"
                  class="card-img-top"
                  :alt="prod.title"
                />
                <div class="card-body">
                  <h5 class="card-title">{{ prod.title }}</h5>
                  <p class="card-text">{{ prod.brief }}</p>
                  <h6 class="text-center text-primary my-3">
                    {{ prod.price }} L.E
                  </h6>
                  <template v-if="prod.inStock">
                    <button class="btn btn-block btn-primary">Buy Now</button>
                  </template>
                  <template v-else>
                    <button class="btn btn-block btn-secondary" disabled="true">
                      Not In Stock
                    </button>
                  </template>
                </div>
              </div>
            </slide>
          </carousel-3d>
        </template>
      </div>
    </div>
  </div>
</template>

<script>
import { Carousel3d, Slide } from "vue-carousel-3d";

export default {
  components: {
    Carousel3d,
    Slide,
  },
  props: ["prods"],
};
</script>

<style></style>
