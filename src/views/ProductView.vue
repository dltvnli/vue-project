<script setup>
  import {useRoute} from "vue-router";
  import axios from "axios";
  import {onMounted, ref} from "vue";
  import cartMethods from '../utils/cart'

  const route = useRoute()
  const isLoaded = ref(false)
  const product = ref({})
  const fetchProduct = async () => {
      isLoaded.value = false
      const product_req = await axios.get(`http://localhost:8000/api/products/${route.params.id}`)
      product.value = product_req.data
      isLoaded.value = true
  }
  onMounted(async () => {
      await fetchProduct()
  })
</script>

<template>
        <div>
      <h1  class = " me-md-3 pt-3 px-3  px-md-5  text-center">Product</h1>
  <div class="position-relative overflow-hidden p-3  m-md-3 text-center bg-body-tertiary">
    <div class="container-sm sticky-sm" style="width: 20%"><img :src="product.image" class="card-img-top" :alt="product.title"></div>
    <div class="col-md-5 p-lg-5 mx-auto my-0">
      <div v-if="isLoaded">
      <h1 class="display-6 fw-normal ">{{ product.title }} {{ product.price }}</h1>
    </div>
    <div v-else>
          ...loading
      </div>
      <p class=" lead fw-normal">{{ product.description }}</p>
      <button class="btn btn-outline-secondary" @click="cartMethods.addToCart(product)">
            Add to cart
          </button>
    </div>
  </div>
      </div>
</template>
