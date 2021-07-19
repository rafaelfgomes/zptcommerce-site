<template>
  <div class="cart container">
    <Title titleName="SEU CARRINHO" />

    <table class="table">
      <thead>
        <tr class="table-active">
          <th scope="col">Produto</th>
          <th scope="col">Preço</th>
          <th scope="col">Quantidade</th>
          <th scope="col">Total</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Mark</td>
          <td>Mark</td>
          <td>Otto</td>
          <td>@mdo</td>
        </tr>
        <tr>
          <td>Mark</td>
          <td>Jacob</td>
          <td>Thornton</td>
          <td>@fat</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
import Title from "@/components/Title";

export default {
  name: "Cart",
  components: {
    Title,
  },
  props: {
    product: Object
  },
  data () {
    return {
      products: []
    }
  },
  computed: {
    productList: () => {
      return this.addProduct(this.product)
    }
  },
  methods: {
    addProduct(product) {
      this.products.push(product)
    }
  }
};
</script>

<style>
</style>