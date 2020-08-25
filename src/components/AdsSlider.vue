<template>
  <div class="container-fluid">
    <div class="py-3 row">
      <div class="col-sm-10 offset-sm-1">
        <vue-flux
          :options="vfOptions"
          :images="vfImages"
          :transitions="vfTransitions"
          :captions="vfCaptions"
          ref="slider"
        >
          <template v-slot:preloader>
            <flux-preloader />
          </template>

          <template v-slot:caption>
            <flux-caption />
          </template>

          <template v-slot:controls>
            <flux-controls />
          </template>

          <template v-slot:pagination>
            <flux-pagination />
          </template>

          <template v-slot:index>
            <flux-index />
          </template>
        </vue-flux>
      </div>
    </div>
  </div>
</template>

<script>
import {
  VueFlux,
  FluxCaption,
  FluxControls,
  FluxIndex,
  FluxPagination,
  FluxPreloader,
} from "vue-flux";

export default {
  components: {
    VueFlux,
    FluxCaption,
    FluxControls,
    FluxIndex,
    FluxPagination,
    FluxPreloader,
  },

  data: () => ({
    vfOptions: {
      autoplay: true,
    },
    vfImages: [
      "https://previews.123rf.com/images/houbacze/houbacze1801/houbacze180100302/93088691-banner-promotion-vector-illustration-.jpg",
      "https://thumbs.dreamstime.com/z/creative-business-concept-businessman-working-laptop-35888471.jpg",
      "https://cdn.hipwallpaper.com/i/86/95/yS7tLJ.gif",
    ],
    vfTransitions: ["fade", "cube", "book", "wave"],
    vfCaptions: [
      "Promotion One Caption (Will Be Replaced With Real data)",
      "Promotion Two Caption (Will Be Replaced With Real data)",
      "Promotion Three Caption (Will Be Replaced With Real data)",
    ],
  }),
};
</script>

<style></style>
