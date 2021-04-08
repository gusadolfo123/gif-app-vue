<template>
  <div class="card">
    <img :src="gif.url" width="200" :alt="gif.title" />
    <a :href="gif.url" target="_blank" rel="noreferrer">
      <p class="card-title">{{ gif.title }}</p>
    </a>
  </div>
</template>

<script>
export default {
  name: "gif-card",
  props: ["gif"],
};
</script>

<style>
</style>