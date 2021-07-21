<template>
  <div class="cart container">
    <Title titleName="SEU CARRINHO" />

    <div
      class="alert alert-dismissible fade show"
      :class="[showAlert ? '' : 'd-none', alertClass]"
      role="alert"
    >
      {{ alertText }}
      <button
        type="button"
        id="btn-alert-close"
        class="btn-close"
        data-bs-dismiss="alert"
        aria-label="Fechar"
      ></button>
    </div>

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
          <tr>
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
              <input @change="calculateTotal(product.price, product.quantity)" class="cart-quantity" ref="cartQuantity" type="number" name="quantity" id="cart-quantity" value="1" min="1" :max="product.quantity">
            </td>
            <td>
              R$&nbsp;<span class="totalAmount" ref="total">{{ formatTotal(total) }}</span>
            </td>
          </tr>
        </tbody>
      </table>

      <div class="checkout d-flex justify-content-end">
        <router-link class="btn btn-outline-secondary me-4" role="button" to="/">
          Voltar
        </router-link>
        <button type="button" @click="checkout()" class="btn btn-outline-success" :class="btnDisabled">Finalizar compra</button>
      </div>

    </div>

    
  </div>
</template>

<script>
import Title from "@/components/Title"
import { apiUrl } from '/config'

export default {
  name: "Cart",
  components: {
    Title,
  },
  data () {
    return {
      product: {},
      alertText: '',
      alertClass: '',
      btnDisabled: '',
      showAlert: false,
      total: 0,
    }
  },
  async mounted() {
    let id = this.$route.params.id
    const response = await fetch(`${apiUrl}/products/${id}`)
    const data = await response.json()
    this.product = data
    this.calculateTotal(this.product.price, this.product.quantity)
  },
  methods: {
    calculateTotal(price, productQuantity) {
      let cartQuantity = parseInt(this.$refs.cartQuantity.value)
      if (this.checkQuantity(cartQuantity, productQuantity)) {
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
    },
    async checkout() {
      this.btnDisabled = "disabled";

      let data = {
        quantity: parseInt(this.$refs.cartQuantity.value),
        amount: this.$refs.total.innerHTML,
        product_id: this.product.id
      }

      const response = await fetch(`${apiUrl}/sales`, {
        method: "POST",
        body: JSON.stringify(data),
        headers: { "Content-Type": "application/json" }
      })

      this.showAlert = true

      if (response.status !== 201) {
        this.errorResponse("Erro finalizar a compra");
        this.btnDisabled = '';
        setTimeout(() => {
          document.getElementById("btn-alert-close").click();
        }, 5000);
        return;
      }

      document.getElementById('cart-quantity').setAttribute('disabled', 'disabled')
      this.successResponse("Compra realizada com sucesso");
    },
    successResponse(message) {
      this.alertText = message;
      this.alertClass = "alert-success";
    },
    errorResponse(message) {
      this.alertText = message;
      this.alertClass = "alert-danger";
    }
  }
};
</script>

<style>
.img-cart {
  width: 50px;
  height: 50px;
}
.cart-quantity {
  width: 70px;
}
</style>