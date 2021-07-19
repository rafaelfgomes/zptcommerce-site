<template>
  <header class="header">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container">
        <router-link class="navbar-brand" to="/">
          <img class="img-fluid logo" src="@/assets/logo.png" alt="Logo" />
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
          class="collapse navbar-collapse d-flex justify-content-center"
          id="navbarSupportedContent"
        >
          <form class="d-flex">
            <input
              class="form-control me-2 search"
              type="search"
              placeholder="Digite sua busca"
              aria-label="Buscar"
            />
            <button class="btn btn-outline-success" type="submit">
              Buscar
            </button>
          </form>
        </div>
        <div class="cart">
          <router-link to="/cart">
            <i class="fas fa-shopping-cart fa-2x cart-icon"></i>
          </router-link>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: "Header",
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