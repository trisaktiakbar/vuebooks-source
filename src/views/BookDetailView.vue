<template>
  <div class="container">
    <div class="row mt-4">
      <nav aria-label="breadcrumb">
        <ol class="breadcrumb bg-transparent px-0">
          <li class="breadcrumb-item text-muted"><router-link to="/" class="text-decoration-none">Home</router-link></li>
          <li class="breadcrumb-item"><router-link to="/books" class="text-decoration-none">Books</router-link></li>
          <li class="breadcrumb-item active">{{ book.title }}</li>
        </ol>
      </nav>
    </div>
    <div class="row mt-3 justify-content-center">
      <div class="col-8 col-md-4 col-lg-3 me-lg-5 mb-5 cursor-pointer">
        <div class="bg-size-cover shadow border overflow-hidden rounded-4 w-100" :style="`min-height: 50vh; background-image: url('${getDefaultCover()}');`">
          <img data-bs-toggle="modal" data-bs-target="#exampleModal" :src="getBookImageURL(book)" alt="" class="w-100 object-fit-cover" style="min-height: 50vh" />
        </div>
      </div>
      <div class="col-md-8">
        <h3>
          <strong class="lh-base">{{ book.title }}</strong>
        </h3>
        <hr class="mb-5" />
        <div>
          <table class="table">
            <tbody>
              <tr>
                <td>
                  <div class="d-flex justify-content-between">
                    <span>Title</span>
                    <span>:</span>
                  </div>
                </td>
                <th>{{ book.title }}</th>
              </tr>
              <tr>
                <td>
                  <div class="d-flex justify-content-between">
                    <span>Author</span>
                    <span>:</span>
                  </div>
                </td>
                <th>
                  <div class="mb-2">
                    <span v-for="(author, index) in this.book.authors || this.book.author_name" :key="index">{{ author }}<span v-if="index < (this.book.authors || this.book.author_name).length - 1">, </span> </span>
                  </div>
                </th>
              </tr>
              <tr>
                <td>
                  <div class="d-flex justify-content-between">
                    <span>Publish Year</span>
                    <span>:</span>
                  </div>
                </td>
                <th>{{ getPublishYear }}</th>
              </tr>
              <tr>
                <td>
                  <div class="d-flex justify-content-between">
                    <span>Edition</span>
                    <span>:</span>
                  </div>
                </td>
                <th>{{ book.edition_count }}</th>
              </tr>
              <tr>
                <td>
                  <div class="d-flex justify-content-between">
                    <span>Publisher</span>
                    <span>:</span>
                  </div>
                </td>
                <th>
                  <div class="mb-2">
                    <span v-for="(publisher, index) in this.book.publisher" :key="index">{{ publisher }}<span v-if="index < this.book.publisher.length - 1">, </span> </span>
                  </div>
                </th>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header">
            <h1 class="modal-title fs-5" id="exampleModalLabel">Book Cover</h1>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body text-center">
            <img :src="getBookImageURL(book)" alt="" class="object-fit-cover rounded-4 bg-size-cover border" :style="`max-height: 65vh; min-height: 40vh; background-image: url('${getDefaultCover()}')`" />
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-success" data-bs-dismiss="modal">Close</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "BookDetailView",

  data() {
    return {
      book: {
        title: "",
        publish_year: "",
        authors: [],
        author_name: [],
        edition: "",
        isbn: [],
        oclc: [],
      },
    };
  },
  methods: {
    getDefaultCover() {
      return require("@/assets/img/default-cover.png");
    },
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

      console.log(url);
      return `https://covers.openlibrary.org/b/${type}/${url}-L.jpg`;
    },
  },

  computed: {
    getPublishYear() {
      return this.book.publish_year > new Date().getFullYear() ? "-" : this.book.publish_year;
    },
  },
  mounted() {
    let id = "/works/" + this.$route.params.id;
    axios
      .get("https://openlibrary.org/search.json?q=" + id)
      .then((response) => {
        this.book = response.data.docs.filter((item) => {
          return item.key == id;
        });
        this.book = this.book[0] ? this.book[0] : [];
        this.title = this.book.title;
        this.book.publish_year = this.book.publish_year[0];
      })
      .catch((error) => {
        console.error(error);
      });
  },
};
</script>

<style></style>
