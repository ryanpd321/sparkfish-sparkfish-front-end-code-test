<template>
  <Header />
  <main>
    <searchBox />
  </main>
</template>
<script>
/**
 * Welcome to the Sparkfish Interview process. This Code
 * Challenge is designed to get to know you. We've left it
 * pretty simple and fairly blank. We've done some setup
 * for you to reduce the time you spend on this challenge.
 *
 * Please finish this by integrating properly with the API
 * and handling search results. The navbar contains some extra
 * UI elements you can create for extra credit. Please note they
 * are NOT required.
 *
 * This challenge really focuses on your front-end skills. But, we
 * do want to make sure you can work with API's with relative ease.
 *
 * Good luck!
 *
 * ~~ The Sparkfish Team
 *
 * @updated 06-01-2022 by Brent
 */
import Header from "./Header.vue";
import searchBox from "./searchBox.vue";

export default {
  components: {
    Header,
    searchBox,
  },
};
</script>

<style>
@import "./assets/base.css";

#app {
  max-width: 1920px;
  margin: 0 auto;
  padding: 0;
  font-weight: normal;
}

header {
  line-height: 1.5;
}
main {
  max-width: 600px;
  margin: 0 auto;
  /* text-align: center; */
  padding: 30px 0;
}
</style>
