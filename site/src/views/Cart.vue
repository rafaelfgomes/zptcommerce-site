<template>
  <div class="cart container">
    <Title titleName="SEU CARRINHO" />

    <div class="cart-content my-5">

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
          <tr >
            <td>
              <img class="img-cart" :src="product.image">
              &nbsp;
              <span>
                {{ product.name }}
              </span>
            </td>
            <td>
              R$&nbsp;{{ product.price }}
            </td>
            <td>
              <input @change="calculateTotal(product.price, product.quantity)" class="cart-quanttiy" ref="cartQuantity" type="number" name="quantity" id="cart-quantity" value="1" min="1" :max="product.quantity">
            </td>
            <td>
              R$&nbsp;{{ formatTotal(total) }}
            </td>
          </tr>
        </tbody>
      </table>

      <div class="checkout d-flex justify-content-end">
        <router-link class="btn btn-outline-secondary me-4" role="button" to="/">
          Voltar
        </router-link>
        <button type="button" class="btn btn-outline-success">Finalizar compra</button>
      </div>

    </div>

    
  </div>
</template>

<script>
import Title from "@/components/Title";

export default {
  name: "Cart",
  components: {
    Title,
  },
  data () {
    return {
      product: {},
      total: 0,
    }
  },
  async mounted() {
    let id = this.$route.params.id
    const response = await fetch(`http://0.0.0.0:8085/api/v1/products/${id}`)
    const data = await response.json()
    this.product = data
    this.calculateTotal(this.product.price, this.product.quantity)
  },
  methods: {
    calculateTotal(price, productQuantity) {
      let cartQuantity = parseInt(this.$refs.cartQuantity.value)
      if (this.checkQuantity(cartQuantity, productQuantity)) {
        console.log(cartQuantity, productQuantity);
        this.total = parseFloat(this.formatPrice(price) * cartQuantity)
        return
      }

      this.$refs.cartQuantity.value = productQuantity
    },
    formatPrice(price) {
      return parseFloat((price).replace(',', '.'))
    },
    formatTotal(total) {
      return ((total.toFixed(2)).toString()).replace('.', ',')
    },
    checkQuantity(quantity, totalQuantity) {
      return (quantity > totalQuantity) ? false : true
    }
  }
};
</script>

<style>
.img-cart {
  width: 50px;
  height: 50px;
}
.cart-quanttiy {
  width: 70px;
}
</style>