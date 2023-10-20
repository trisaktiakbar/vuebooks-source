<template>
  <div class="container">
    <div class="row align-items-center justify-content-center" style="min-height: 90vh">
      <div class="col-lg-8">
        <h1 class="fw-bold mb-4">Contact Us</h1>
        <h5 class="mb-5 lh-base">"Thank you for visiting our website. Please feel free to contact us if you have any questions, comments, or special requests. We are pleased to hear from you."</h5>
        <div class="d-flex">
          <a href="mailto:trisaktiakbar01@gmail.com" target="_blank" class="btn btn-outline-success me-2 btn-lg border-2 rounded-circle d-flex justify-content-center align-items-center circle-icon">
            <i class="bi bi-envelope"></i>
          </a>
          <a href="https://wa.me/6285251706721" target="_blank" class="btn btn-outline-success me-2 btn-lg border-2 rounded-circle d-flex justify-content-center align-items-center circle-icon">
            <i class="bi bi-whatsapp"></i>
          </a>
          <a href="https://www.instagram.com/trisakti_akbar" target="_blank" class="btn btn-outline-success me-2 btn-lg border-2 rounded-circle d-flex justify-content-center align-items-center circle-icon">
            <i class="bi bi-instagram"></i>
          </a>
          <a href="#" class="btn btn-outline-success me-2 btn-lg border-2 rounded-circle d-flex justify-content-center align-items-center circle-icon">
            <i class="bi bi-facebook"></i>
          </a>
          <a href="https://twitter.com/trisakti_akbar" target="_blank" class="btn btn-outline-success me-2 btn-lg border-2 rounded-circle d-flex justify-content-center align-items-center circle-icon">
            <i class="bi bi-twitter"></i>
          </a>
        </div>
      </div>
      <div class="col-6 col-sm-6 col-lg-3 col-xl-2 offset-lg-1 order-first order-lg-last">
        <div class="rounded-circle overflow-hidden border border-success border-4">
          <div class="rounded-circle overflow-hidden border border-white border-4">
            <img :src="getOwnerImage()" alt="Trisakti Akbar" class="w-100" />
          </div>
        </div>
        <div class="d-flex justify-content-center" style="transform: translateY(-28px) rotate(3deg)">
          <div class="text-center">
            <h4 class="bg-success text-white px-2 mb-0">Trisakti Akbar</h4>
            <h6 class="fw-normal">Website Owner</h6>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BookDetailView",

  data() {
    return {};
  },
  methods: {
    getOwnerImage() {
      return require("@/assets/img/owner.jpg");
    },
  },
};
</script>

<style scoped>
.circle-icon {
  width: 44px !important;
  height: 44px !important;
}
</style>
