<template>
  <div class="container">
    <div class="row align-items-center" style="min-height: 90vh">
      <div class="col-md-6">
        <h1 class="fw-bold mb-3">Explore the Universe!</h1>
        <h2 class="mb-5">It's a Chapter of Your Life</h2>
        <router-link class="btn btn-lg btn-success" to="/books">
          <div class="d-flex align-items-center">
            <i class="bi bi-arrow-right"></i>
            <div class="ms-2 fw-semibold">Explore More</div>
          </div>
        </router-link>
      </div>
      <div class="col-md-6 px-5 order-first order-lg-last mt-5 mt-md-1">
        <img :src="getHeroImage()" alt="VueBooks" class="w-100 ms-auto" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeroComponent",
  methods: {
    getHeroImage() {
      return require("@/assets/img/hero.svg");
    },
  },
};
</script>

<style></style>
