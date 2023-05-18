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
  <h1  class = " me-md-3 pt-3 px-3  px-md-5  text-center">Product</h1>
      <section class="py-0">
            <div class="container px-4 px-lg-5 my-0">
                <div class="row gx-4 gx-lg-5 mx-auto align-items-center">
                    <div class="col-md-4"><img :src="product.image" class="card-img-top ml-5  mb-md-0 " :alt="product.title"/></div>
                    <div class="col-md-8">
                      <div class="col-md-9 p-lg-5 ms-auto my-0 ">
                        <div v-if="isLoaded">
                        <h1 class="display-5 fw-bolder ">{{ product.title }}</h1>
                        <div class="fs-5 mb-5">
                            <span > {{ product.price }} тг</span>
                        </div>
                        <p class="lead">{{ product.description }}</p>
                        <div class="d-flex">
                            <input class="form-control text-center me-3" id="inputQuantity" type="num" value="1" style="max-width: 3rem" />
                            <button class="btn btn-outline-dark flex-shrink-0" @click="cartMethods.addToCart(product)">
                                <i class="bi-cart-fill me-1"></i>
                                Add to cart
                            </button>
                        </div>
                    </div>
                </div>
            </div>
            </div>
            </div>
        </section>
</template>
