<template>
  <div class="list my-5">
    <div class="row row-cols-1 row-cols-md-3 g-4">
      <div class="col" :key="product.id" v-for="product in products">
        <div class="card h-100">
          <img :src="product.image" class="card-img-top img-product" />
          <div class="card-body">
            <h4 class="card-title">{{ product.name }}</h4>
            <p class="card-text fw-bold fs-3">
              R$&nbsp;{{ product.price }}
            </p>
            <p class="card-text mt-3 d-flex justify-content-center">
              <button @click="produtDetails(product.id)" class="btn btn-outline-info w-50">
                Detalhes
              </button>
            </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Products",
  data () {
    return {
      products: []
    }
  },
  async created () {
    this.products = await this.fetchProducts()
  },
  methods: {
    async fetchProducts() {
      const response = await fetch('http://0.0.0.0:8085/api/v1/products/actives')
      const data = await response.json()
      return data
    },
    produtDetails(product) {
      this.$router.push({
        path: `/product/details/${product}`
      })      
    }
  }
};
</script>

<style>
.img-product {
  width: 400px;
  height: 400px;
}
</style>
