<template>
  <header class="header">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container">
        <router-link class="navbar-brand" to="/">
          <img class="img-fluid logo" src="@/assets/logo.png" alt="Logo" />
          ZPT Commerce
        </router-link>
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarSupportedContent"
          aria-controls="navbarSupportedContent"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div
          class="collapse navbar-collapse d-flex justify-content-end"
          id="navbarSupportedContent"
        >
          <form class="d-flex">
            <input
              class="form-control me-2 search"
              type="search"
              ref="inputSearch"
              placeholder="Digite sua busca"
              aria-label="Buscar"
              :value="productFilter"
              required
            />
            <button class="btn btn-outline-success" @click="searchByName(this.$refs.inputSearch.value)" type="button">
              Buscar
            </button>
          </form>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      productFilter: ''
    }
  },
  methods: {
    searchByName(productFilter) {
      if (productFilter.length === 0) {
        return
      }
      this.$refs.inputSearch.value = ''
      this.$router.push({
        name: 'Search',
        params: {
          filter: productFilter
        }
      })      
    }
  }
};
</script>

<style>
.logo {
  width: 35px;
}

.header {
  width: 100%;
}

.search {
  width: 800px;
}

.cart-icon {
  color: white;
  width: 30px;
}
</style>