<template>
  <!-- Simple UI With Bootstrap CSS Classes (Componenet Block)-->

  <div class="container-fluid">
    <div class="py-3 row bg-gray">
      <h4 class="text-success mt-0 mb-3">Air Conditioners: (Vue-Carousel)</h4>
      <div class="col-sm-10 offset-sm-1 py-3 bg-white">
        <!-- Something to Render incase Products Didn't Fetched (Error Boundary) -->
        <template v-if="!prods.length">
          <p>Loading</p>
        </template>
        <!-- Render List and it's Products   -->
        <template v-else>
          <carousel
            :perPageCustom="[
              [480, 1],
              [576, 2],
              [768, 3],
              [992, 5],
            ]"
            :autoplay="true"
            :autoplayTimeout="3000"
            :minSwipeDistance="20"
            :scrollPerPage="false"
            :navigationEnabled="true"
            :autoplayHoverPause="true"
            :navigationClickTargetSize="20"
            :paginationEnabled="false"
          >
            <slide v-for="(prod, index) in prods" :key="index">
              <div class="card mx-2 p-2">
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
          </carousel>
        </template>
      </div>
    </div>
  </div>

  <!-- Simple UI With Bootstrap CSS Classes (Componenet Block)-->
</template>

<script>
import { Carousel, Slide } from "vue-carousel";

export default {
  components: {
    Carousel,
    Slide,
  },
  props: ["prods"],
};
</script>

<style>
@media only screen and (max-width: 480px) {
  .VueCarousel-navigation-next {
    display: none !important;
  }
}
</style>
