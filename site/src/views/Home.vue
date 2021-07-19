<template>
  <div class="produt-list container">
    <Title titleName="LISTA DE PRODUTOS" />
    <Products />
  </div>
</template>

<script>
import Products from "@/components/Products";
import Title from "@/components/Title";

export default {
  name: "Home",
  components: {
    Products,
    Title,
  },
};
</script>
