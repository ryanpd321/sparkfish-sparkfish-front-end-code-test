<template>
  <div id="searchBox">
    <label>Enter search parameter here</label>
    <input
      type="text"
      name="searchBoxQuery"
      id="searchBoxQuery"
      @keyup.enter="onEnter"
      placeholder="Enter here.."
    />
  </div>
  <Results :searchResults="searchResults" :searchQuery="searchQuery" :isLoading="isLoading" />
</template>

<script>
import { ref } from "vue";
import Results from "./Results.vue";
const APIBaseUrl = "https://api.adviceslip.com/advice/";

export default {
  setup() {
    let searchQuery = ref("");
    let searchResults = ref();
    let isLoading = ref(false);
    return {
      searchQuery,
      searchResults,
      isLoading
    };
  },
  components: {
    Results,
  },

  mounted() {
    this.searchQuery = "";
    this.search();
  },
  methods: {
    onEnter(e) {
      e.preventDefault();
      this.isLoading = true;
      this.searchQuery = e.target.value;
      this.search();
    },
    search() {
      if (!this.searchQuery) return;
      try {
        fetch(APIBaseUrl + `search/${this.searchQuery}`)
          .then((response) => response.json())
          .then((data) => {
            this.isLoading = false;
            this.searchResults = data;
          });
      } catch (e) {
        console.warn(e);
      }
    },
  },
};
</script>

<style lang="css" scoped>
@import "./assets/base.css";
#searchBoxQuery {
  min-height: 35px;
  max-width: 300px;
  display: block;
  width: 100%;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  font-weight: 400;
  line-height: 1.5;
  color: #212529;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ced4da;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
}
</style>
