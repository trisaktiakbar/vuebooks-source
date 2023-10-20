<template>
  <div class="container">
    <div class="row align-items-center justify-content-center" style="min-height: 90vh">
      <div class="col-md-7">
        <h1 class="fw-bold mb-3">About <span class="text-success">VueBooks</span></h1>
        <h5 class="lh-base mb-5">
          Welcome to <router-link to="/" class="text-success text-decoration-none">VueBooks</router-link>. We provide book data to assist you in discovering and exploring book titles, authors, publication years, publishers, and book covers
          that interest you.
        </h5>
        <h5 class="lh-base mb-5 fw-bold text-success"><i>"The more books, the more references!"</i></h5>
      </div>
      <div class="col-8 col-md-5 col-lg-4 offset-lg-1 order-first order-md-last pb-lg-5"><img :src="getImage('hero-2.svg')" alt="VueBooks" class="w-100 ms-auto my-5 pb-5" /></div>
    </div>
  </div>
  <div class="container-fluid py-5 bg-light">
    <div class="container py-5">
      <div class="row">
        <h1 class="fw-bold mb-3 text-center"><span class="text-success">Thanks</span> to...</h1>
        <div class="row py-3 py-md-5 mb-3 mb-md-5 justify-content-evenly align-items-center">
          <div class="col-4 col-sm-3 col-lg-2">
            <a href="https://vuejs.org" target="_blank"> <img :src="getImage('vuejs.png')" alt="" srcset="" class="w-100 grayscale" /> </a>
          </div>
          <div class="col-4 col-sm-3 col-lg-2">
            <a href="https://getboorstrap.com" target="_blank">
              <img :src="getImage('bootstrap.png')" alt="" srcset="" class="w-100 grayscale" />
            </a>
          </div>
          <div class="col-4 col-sm-3 col-lg-2">
            <a href="https://openlibrary.org" target="_blank"> <img :src="getImage('open-library.png')" alt="" srcset="" class="w-100 grayscale" /> </a>
          </div>
        </div>

        <h5 class="lh-base mb-5">
          The website owner expresses gratitude to <a class="text-decoration-none fw-semibold text-success" href="https://vuejs.org" target="_blank">VueJS</a>,
          <a class="text-decoration-none fw-semibold text-success" href="https://getbootstrap.com" target="_blank">Bootstrap</a>, and
          <a class="text-decoration-none fw-semibold text-success" href="https://openlibrary.org" target="_blank">OpenLibrary</a> for providing resources and several ready-to-use libraries that have supported the development of this
          website.
        </h5>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    getImage(image) {
      return require("@/assets/img/" + image);
    },
  },
};
</script>

<style scoped>
.grayscale {
  filter: grayscale(100%);
  transition: 0.3s;
}

.grayscale:hover {
  filter: grayscale(0);
}
</style>
