<template>
  <a :href="`#${category}`">
    {{ category }}
  </a>
</template>

<script>
export default {
  props: ["category"],
};
</script>

<style scoped>
a {
  font-weight: bold;
  background-color: rgb(128, 190, 128);
  border-radius: 50px;
  text-align: center;
  padding-left: 20px;
  padding-right: 20px;
  padding-top: 10px;
  padding-bottom: 10px;
}
</style>