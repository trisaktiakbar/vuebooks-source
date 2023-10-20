<template>
  <div>
    <nav class="navbar navbar-expand-lg bg-white">
      <div class="container">
        <a class="navbar-brand text-success fw-bold" href="#">VueBooks</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
            <li class="nav-item me-3">
              <router-link to="/" class="nav-link">Home</router-link>
            </li>
            <li class="nav-item me-3">
              <router-link to="/books" class="nav-link">Books</router-link>
            </li>
            <li class="nav-item me-3">
              <router-link to="/about" class="nav-link">About</router-link>
            </li>
            <li class="nav-item me-3">
              <router-link to="/contact" class="nav-link">Contact</router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "NavbarComponent",
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
