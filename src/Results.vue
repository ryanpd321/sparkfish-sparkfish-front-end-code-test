<template>
  <div id="searchResults">
    <ul>
      <li>Search Query: {{ searchQuery }}</li>
      <li>Result Count: {{ searchResults.total_results }}</li>
    </ul>
    <!-- // Add your search results code here -->
    <div v-if="searchResults.slips && searchResults.slips.length">
      <div>Result Advice</div>
      <table>
        <thead>
          <tr>
            <th>Advice</th>
            <th>Publish Data</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="item of searchResults.slips" :key="item.id">
            <td>{{ item.advice }}</td>
            <td>{{ item.date }}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <div class="loader-wrapper" v-if="isLoading">
        <div class="loader">
            <span></span>
        </div>
    </div>
  </div>
</template>

<script>

export default {
  props: {
    searchResults: {
      default: {
        total_results: 0,
        slips: [],
      },
    },
    searchQuery: {
      default: "",
    },
    isLoading: {
        default: false,
        type: Boolean
    }
  },
};
</script>
<style scoped>
#searchResults {
  text-align: left;
}
#searchResults ul {
  list-style-type: none;
  padding: 0;
}
table {
  caption-side: bottom;
  border-collapse: collapse;
  color: #212529;
  vertical-align: top;
  border: 1px solid #dee2e6;
  width: 100%;
  margin-top: 10px;
}
table thead {
  background: #1b4c5a;
  color: #fff;
}
table th,
table td {
  padding: 8px;
  border: 1px solid #dee2e6;
  min-width: 100px;
}
.loader-wrapper {
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: rgba(0,0,0,0.2);
}
.loader {
  width: 48px;
  height: 48px;
  border: 5px solid #fff;
  border-bottom-color: #ff3d00;
  border-radius: 50%;
  display: inline-block;
  box-sizing: border-box;
  animation: rotation 1s linear infinite;
}
@keyframes rotation {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
