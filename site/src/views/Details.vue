<template>
  <div class="product-detail my-5 container">
    <Title titleName="DETALHES DO PRODUTO" />

    <div class="product-cover bg-light d-flex justify-content-center align-items-center">
      <div class="card bg-transparent border-light py-5" style="max-width: 50rem">
        <div class="row g-0">
          <div class="col-md-4">
            <img :src="product.image" class="img-fluid rounded-start img-product" :alt="product.name" />
          </div>
          <div class="col-md-8">
            <div class="card-body product-data d-flex flex-column justify-content-around">
              <h3 class="card-title">{{ product.name }}</h3>
              <p class="card-text description">
                {{ product.description }}
              </p>
              <p class="card-text fw-bold fs-4 price">
                R$ {{ product.price }}
              </p>
              <p class="card-text">
                <button type="button" class="btn btn-outline-success">Adicionar ao carrinho</button>
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Title from "@/components/Title";



export default {
  name: "Details",
  data () {
    return {
      product: {
        image: 'https://via.placeholder.com/400x500',
        name: 'Produto 1',
        description: 'Descrição longa do produto 1',
        price: '40,00'
      }
    }
  },
  // props: {
  //   product: Object
  // },
  components: {
    Title,
  },
};
</script>

<style>
.product-cover {
  height: 500px;
}

.product-data {
  height: 100%;
}

.img-product {
  width: 500;
  height: 400;
}

</style>