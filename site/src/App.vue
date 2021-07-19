<template>
  <Header />
  <main class="container">
    <Menu />
    <Cover :text="setCoverName()" />
    <router-view/>
  </main>
  <Footer />
</template>

<script>
import Header from '@/components/Header'
import Menu from '@/components/Menu'
import Cover from '@/components/Cover'
import Footer from '@/components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Menu,
    Cover,
    Footer
  },
  methods: {
    setCoverName() {
      let route = this.$route.name

      switch (route) {
        case "About":
          return "SOBRE"

        case "Cart":
          return "CARRINHO"

        case "Details":
          return "DETALHES"
      
        default:
          return "PRODUTOS"
      }
    }
  }
}
</script>

<style lang="scss">
* {
 font-family: 'Times New Roman', Times, serif; 
}
</style>
