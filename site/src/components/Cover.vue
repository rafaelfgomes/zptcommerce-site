<template>
  <div class="container cover">
    <div class="card bg-light border-white text-black">
    <img src="@/assets/cover.png" class="card-img" alt="Cover Image Pages">
    <div class="card-img-overlay d-flex flex-column justify-content-end">
      <p class="card-text h1">{{ text }}</p>
    </div>
</div>
  </div>
</template>

<script>
export default {
  name: "Cover",
  props: {
    text: String
  }
}
</script>

<style>

</style>