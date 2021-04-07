<template>
  <div class="grid-gifs">
    <gif-card v-for="gif in gifs" :key="gif.id" :gif="gif" />
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
  props: ["category", "loading"],
  data() {
    return {
      gifs: [],
    };
  },
  watch: {
    category: function (newVal) {
      this.$emit("loading", true);
      getGifs(newVal).then((data) => {
        data.forEach(({ id, title, url }) => {
          this.$emit("loading", false);
          this.gifs.push({
            id,
            title,
            url,
          });
        });
      });
    },
  },
};
</script>

<style>
</style>