<template>
  <router-link :to="'/books/detail' + data.key + '/' + data.title" class="text-decoration-none">
    <div class="text-center">
      <div class="bg-size-cover bg-bottom" :style="`background-image: url('${getDefaultCover()}')`">
        <div class="card-book w-100 rounded-4 overflow-hidden" :alt="data.title" :style="'background-image: ' + getBookImageURL(data)">
          <div class="bg-dark bg-opacity-75 card-img-overflow d-flex align-items-center">
            <button class="btn btn-sm btn-outline-light mx-auto bg-transparent text-white rounded-pill px-3 py-1">
              <div class="d-flex align-items-center small">
                <i class="bi bi-eye"></i>
                <div class="ms-1">Lihat Detail</div>
              </div>
            </button>
          </div>
        </div>
      </div>
      <div class="card-book-text px-1">
        <h6 class="text-start mt-2 fw-bold lh-base mb-0 text-truncate-3" :title="data.title">{{ data.title }}</h6>
        <p class="text-start text-muted text-author text-truncate-2 mt-2">
          <span v-for="(author, index) in data.authors || data.author_name" :key="author.key">{{ author.name || author }}<span v-if="index < (data.authors || data.author_name).length - 1">, </span> </span>
        </p>
      </div>
    </div>
  </router-link>
</template>

<script>
export default {
  name: "BookCardComponent",
  props: ["data"],
  methods: {
    getBookImageURL(data) {
      let type = "";
      let url = "";
      if (data.isbn) {
        type = "isbn";
        url = data.isbn[0];
      }
      if (data.cover_id) {
        type = "id";
        url = data.cover_id;
      }
      if (data.cover_i) {
        type = "id";
        url = data.cover_i;
      }
      return `url('https://covers.openlibrary.org/b/${type}/${url}-M.jpg')`;
    },
    getDefaultCover() {
      return require("@/assets/img/default-cover.png");
    },
  },
};
</script>

<style scoped></style>
