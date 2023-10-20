<template>
  <HeroComponent />

  <div class="container mt-5">
    <div class="row mb-3">
      <h2>Non <span class="fw-bold">Fiction</span></h2>
      <hr />
    </div>
    <LoadingComponent :data="books.non_fiction" />
    <div class="row mb-3">
      <div v-for="book in books.non_fiction" :key="book.key" class="col-sm-6 col-md-6 col-lg-4 col-xl-2 mb-3">
        <BookCardComponent :data="book" />
      </div>
    </div>

    <div class="row mb-3">
      <h2><span class="fw-bold">History</span> Books</h2>
      <hr />
    </div>
    <LoadingComponent :data="books.history" />
    <div class="row mb-3">
      <div v-for="book in books.history" :key="book.key" class="col-sm-6 col-md-6 col-lg-4 col-xl-2 mb-3">
        <BookCardComponent :data="book" />
      </div>
    </div>

    <div class="row mb-3">
      <h2><span class="fw-bold">Science</span></h2>
      <hr />
    </div>
    <LoadingComponent :data="books.science" />
    <div class="row mb-3">
      <div v-for="book in books.science" :key="book.key" class="col-sm-6 col-md-6 col-lg-4 col-xl-2 mb-3">
        <BookCardComponent :data="book" />
      </div>
    </div>

    <div class="row mb-3">
      <h2><span class="fw-bold">Fashion</span> Books</h2>
      <hr />
    </div>
    <LoadingComponent :data="books.fashion" />
    <div class="row mb-3">
      <div v-for="book in books.fashion" :key="book.key" class="col-sm-6 col-md-6 col-lg-4 col-xl-2 mb-3">
        <BookCardComponent :data="book" />
      </div>
    </div>

    <div class="row mb-3">
      <h2>About <span class="fw-bold">Love</span></h2>
      <hr />
    </div>
    <LoadingComponent :data="books.love" />
    <div class="row mb-3">
      <div v-for="book in books.love" :key="book.key" class="col-sm-6 col-md-6 col-lg-4 col-xl-2 mb-3">
        <BookCardComponent :data="book" />
      </div>
    </div>

    <div class="row mb-3">
      <h2><span class="fw-bold">Fiction</span> Books</h2>
      <hr />
    </div>
    <LoadingComponent :data="books.fiction" />
    <div class="row mb-3">
      <div v-for="book in books.fiction" :key="book.key" class="col-sm-6 col-md-6 col-lg-4 col-xl-2 mb-3">
        <BookCardComponent :data="book" />
      </div>
    </div>
  </div>
</template>

<script>
import HeroComponent from "@/components/HeroComponent.vue";
import BookCardComponent from "@/components/BookCardComponent.vue";
import LoadingComponent from "@/components/LoadingComponent.vue";
import axios from "axios";

export default {
  name: "HomeView",
  components: {
    HeroComponent,
    BookCardComponent,
    LoadingComponent,
  },
  data() {
    return {
      books: [],
    };
  },
  methods: {},

  mounted() {
    axios
      .get("https://openlibrary.org/subjects/non_fiction.json?details=true&limit=12")
      .then((response) => {
        this.books.non_fiction = response.data.works;
        console.log(this.books.non_fiction);
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://openlibrary.org/subjects/history.json?details=true&limit=12")
      .then((response) => {
        this.books.history = response.data.works;
        console.log(this.books.history);
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://openlibrary.org/subjects/science.json?details=true&limit=12")
      .then((response) => {
        this.books.science = response.data.works;
        console.log(this.books.science);
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://openlibrary.org/subjects/fashion.json?details=true&limit=12")
      .then((response) => {
        this.books.fashion = response.data.works;
        console.log(this.books.fashion);
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://openlibrary.org/subjects/love.json?details=true&limit=12")
      .then((response) => {
        this.books.love = response.data.works;
        console.log(this.books.love);
      })
      .catch((error) => {
        console.error(error);
      });
    axios
      .get("https://openlibrary.org/subjects/fiction.json?details=true&limit=12")
      .then((response) => {
        this.books.fiction = response.data.works;
        console.log(this.books.fiction);
      })
      .catch((error) => {
        console.error(error);
      });
  },
};
</script>

<style></style>
