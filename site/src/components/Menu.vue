<template>
  <div class="menu mt-3 mb-3">
    <nav
      class="navbar navbar-expand-lg navbar-light"
      style="background-color: white"
    >
      <div class="container-fluid">
        <div class="collapse navbar-collapse d-flex justify-content-center">
          <ul class="navbar-nav d-flex justify-content-center">
            <li class="nav-item">
              <router-link class="nav-link link-menu" to="/">
                Home
              </router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link link-menu" to="/about">
                Sobre
              </router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {
  name: "Menu",
};
</script>

<style>
.link-menu {
  font-size: 30px;
}
</style>