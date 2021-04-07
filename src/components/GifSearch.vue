<template>
  <form @submit.prevent="handleSubmit">
    <input type="text" v-model="category" required />
  </form>
</template>

<script>
export default {
  name: "gif-search",
  data() {
    return {
      category: "",
    };
  },
  methods: {
    handleSubmit(e) {
      this.$emit("submit", this.category);
    },
  },
};
</script>

<style>
</style>