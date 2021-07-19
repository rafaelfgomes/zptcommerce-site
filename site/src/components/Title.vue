<template>
  <h2 class="d-flex justify-content-center my-4">
    <span>{{ titleName }}</span>
  </h2>
</template>

<script>
export default {
  name: "Title",
  props: {
    titleName: String,
  },
};
</script>

<style>
</style>