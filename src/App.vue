<template>
  <div id="app">
    <h1 :class="color">Gif App</h1>
    <button @click="changeColorAndOrder">Reverse Order</button>
    <hr />
    <div class="history-search" id="history-search">
      <gif-history v-for="category in categories" :category="category" />
    </div>
    <hr />
    <GifSearch @submit="handleSubmit" />
    <hr />
    <GifGrid
      v-for="category in categories"
      :key="category"
      :category="category"
    />
  </div>
</template>

<script>
import GifGrid from "./components/GifGrid.vue";
import GifSearch from "./components/GifSearch.vue";
import GifHistory from "./components/GifHistory.vue";

export default {
  name: "App",
  components: {
    GifGrid,
    GifSearch,
    GifHistory,
  },
  data() {
    return {
      categories: [],
      color: "text-red",
    };
  },
  methods: {
    handleSubmit(newTitle) {
      if (!(this.categories.indexOf(newTitle) !== -1)) {
        this.categories.unshift(newTitle);
      }
    },
    changeColorAndOrder() {
      if (this.color == "text-white") this.color = "text-red";
      else this.color = "text-white";
      this.categories.reverse();
    },
  },
  // mounted() {
  //   document
  //     .getElementById("history-search")
  //     .addEventListener("click", function (e) {
  //       if (e.target.tagName === "A") {
  //         document.querySelector(e.target.getAttribute("href")).scrollIntoView({
  //           behavior: "smooth",
  //         });
  //       }
  //     });
  // },
  // destroyed() {
  //   document.removeEventListener("click");
  // },
};
</script>

<style>
.history-search {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  width: 100%;
  gap: 10px;
}

button {
  border-radius: 50px;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 10px;
  padding-bottom: 10px;
  font-weight: bold;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 60px;
  width: 90vw;
  margin: 0 auto;
  background-color: rgb(97, 97, 97);
  padding: 10px;
}

body {
  background-color: rgb(61, 61, 61);
  color: rgb(226, 226, 226);
  margin: 0;
  padding: 40px;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, "Courier New",
    monospace;
}

h1 {
  text-align: center;
}

p {
  margin: 0px !important;
  padding: 0px !important;
}

input {
  width: 100%;
  font-size: 1.2rem;
  color: grey;
}

.grid-gifs {
  /* line-height: 0; */
  line-height: 1;
  -webkit-column-count: 5;
  -webkit-column-gap: 10px;
  -moz-column-count: 5;
  -moz-column-gap: 10px;
  column-count: 5;
  column-gap: 10px;
}

.card {
  position: relative;
  z-index: 1;
  /* border: 1px solid whitesmoke; */
  border-radius: 6px;
  /* align-content: center; */
  overflow: hidden;
  text-align: center;
  /* width: 220px; */
  margin-bottom: 10px;
}

.card-title {
  position: absolute;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 2;
  /* width: 100%; */
  height: 50px;
  left: 0;
  right: 0;
  bottom: 0;
  font-size: 14px;
  font-weight: bold;
  text-overflow: ellipsis;
  background: rgb(2, 0, 36);
  background: linear-gradient(
    0deg,
    rgb(19, 19, 19) 0%,
    rgba(42, 42, 42, 0.866) 35%,
    rgba(255, 255, 255, 0) 100%
  );
  opacity: 0;
  transition: opacity 150ms ease-in 0s;
}

.card:hover .card-title {
  opacity: 1;
  transition: opacity 150ms ease-in 0s;
}

.card > img {
  width: 100% !important;
  height: auto !important;
}

a {
  text-decoration: none;
  color: whitesmoke;
}

.text-red {
  color: rgb(128, 190, 128);
}

.text-white {
  color: whitesmoke;
}

@media (max-width: 1200px) {
  .grid-gifs {
    -moz-column-count: 4;
    -webkit-column-count: 4;
    column-count: 4;
  }
}
@media (max-width: 1000px) {
  .grid-gifs {
    -moz-column-count: 3;
    -webkit-column-count: 3;
    column-count: 3;
  }
}
@media (max-width: 800px) {
  .grid-gifs {
    -moz-column-count: 2;
    -webkit-column-count: 2;
    column-count: 2;
  }
}
@media (max-width: 400px) {
  .grid-gifs {
    -moz-column-count: 1;
    -webkit-column-count: 1;
    column-count: 1;
  }
}
</style>
