<template>
  <div class="list my-5">
    <div v-if="this.products.length === 0">
      <h2>Nenhum produto encontrado</h2>
    </div>
    <div v-else class="row row-cols-1 row-cols-md-3 g-4">
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
import { apiUrl } from '/config'

export default {
  name: "Search",
  data () {
    return {
      products: []
    }
  },
  async created () {
    console.log(this.$route.params.filter)
    this.products = await this.fetchProductsFilter(this.$route.params.filter)
    console.log(this.products.length)
  },
  methods: {
    async fetchProductsFilter(filter) {
      const response = await fetch(`${apiUrl}/products/search/${filter}`)
      const data = await response.json()
      return data
    },
    produtDetails(id) {
      this.$router.push({
        path: `/product/details/${id}`
      })      
    }
  }
};
</script>

<style>
</style>