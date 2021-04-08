<template>
  <div :id="category">
    <h3>{{ loading ? "Loading..." : category }}</h3>
    <div class="grid-gifs">
      <gif-card v-for="gif in gifs" :key="gif.id" :gif="gif" />
    </div>
  </div>
</template>

<script>
import GifCard from "./GifCard.vue";
import getGifs from "./../helpers/fetchData.js";

export default {
  name: "gif-grid",
  components: {
    GifCard,
  },
  props: ["category"],
  data() {
    return {
      gifs: [],
      loading: true,
    };
  },
  mounted() {
    this.loading = true;
    getGifs(this.category).then((data) => {
      data.forEach(({ id, title, url }) => {
        this.loading = false;
        this.gifs.push({
          id,
          title,
          url,
        });
      });
    });
  },
};
</script>

<style>
</style>