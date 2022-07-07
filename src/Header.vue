<template>
  <header>
    <nav>
      <div class="logo">
        <img src="./assets/logo.webp" alt="Sparkfish Logo" />
      </div>
      <ul>
        <li><a href=""> Daily Advice</a></li>
        <li><a href=""> Advice Search</a></li>
        <li><a href=""> Random Advice</a></li>
      </ul>
      <!-- // Style the navbar -->
    </nav>
  </header>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    let searchQuery = ref("");
    let searchResults = ref({});

    return {
      searchQuery,
      searchResults,
    };
  },
  mounted() {},
  methods: {},
};
</script>

<style lang="css" scoped>
@import "./assets/base.css";
nav {
  height: 90px;
  box-sizing: border-box;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-right: 30px;
  box-shadow: 0 2px 6px -1px rgba(0, 0, 0, 0.2);
}
nav ul {
    display: flex;
    list-style-type: none;
    gap: 20px;
}
nav ul a {
    color: #434b4d;
    font-size: 16px;
    text-decoration: none;
}
.logo img {
  width: 100%;
  height: 90px;
}
</style>
