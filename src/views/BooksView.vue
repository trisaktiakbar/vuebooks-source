<template>
  <div class="container mt-5">
    <div class="row mt-3">
      <div class="col">
        <div class="input-group mb-3">
          <input @keyup="searchBooks" v-model="search" type="text" class="form-control" placeholder="Search books ..." aria-label="Cari" aria-describedby="basic-addon1" />
          <span class="input-group-text" id="basic-addon1"><i class="bi bi-search"></i></span>
        </div>
      </div>
    </div>
    <LoadingComponent :data="books.length" class="mt-3" />
    <div class="row mt-3 justify-content-center">
      <div v-for="book in books" :key="book.key" class="col-sm-6 col-md-6 col-lg-3 col-xl-2 mb-3">
        <BookCardComponent :data="book" />
      </div>
    </div>
    <div v-show="books.length" class="row mt-3 mb-5">
      <div class="col text-center">
        <button @click="loadMore()" class="btn btn-outline-success d-inline border-0">Load More ...</button>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import BookCardComponent from "@/components/BookCardComponent.vue";
import LoadingComponent from "@/components/LoadingComponent.vue";

export default {
  name: "BooksView",
  components: { BookCardComponent, LoadingComponent },
  methods: {
    loadBooks() {
      let keyword;
      this.search == "" ? (keyword = "*") : (keyword = this.search);
      axios
        .get("https://openlibrary.org/search.json?q=" + keyword + "&sort=new&page=" + this.page)
        .then((response) => {
          this.books = response.data.docs;
          console.log(this.books);
        })
        .catch((error) => {
          console.error(error);
        })
        .finally(() => this.loadBooks);
    },
    updateBooks() {
      let keyword;
      this.search == "" ? (keyword = "*") : (keyword = this.search);
      axios
        .get("https://openlibrary.org/search.json?q=" + keyword + "&sort=new&page=" + this.page)
        .then((response) => {
          this.books = this.books.concat(response.data.docs);
          console.log(this.books);
        })
        .catch((error) => {
          console.error(error);
        });
    },

    searchBooks() {
      this.books = [];
      this.loadBooks();
    },

    loadMore() {
      this.page++;
      this.updateBooks();
    },
  },
  data() {
    return {
      books: [],
      search: "",
      page: 1,
    };
  },
  mounted() {
    this.loadBooks();
  },
};
</script>

<style></style>
