<script setup>
import { onMounted, ref } from 'vue'
import axios from 'axios'

const wishList = ref([])
const isLoaded = ref(false)

const getWishList = async () => {
  isLoaded.value = false
  const response = await axios.get('http://localhost:8000/api/wishlist/', {
    headers: {
      Authorization: `Bearer ${localStorage.getItem('access_token')}`
    }
  })
  response.data.map(async (product) => {
    const { data } = await axios.get('http://localhost:8000/api/products/' + product)
    wishList.value.push(data)
  })
  console.log(wishList.value);
  isLoaded.value = true
}

onMounted(async () => {
  await getWishList()
})
</script>

<template>
  <div>
    <h2 style="text-align: center;">WishList</h2>
    <div v-if="isLoaded">

      <div style="text-align: center;" class="card-group container" v-for="product in wishList" :key="product.id">
          <div class="card" style="width: 50%; border: 1px solid black; margin: 2%; margin-left: 15%; margin-right: 15%;"> 
    <img :src="product.image" style="width: 300px; "  class="card-img-top" :alt="product.title">
    <div class="card-body justify-content-center ">
        <p class="card-title">{{ product.title }}</p>
        <h3 class="card-text">{{ product.price }}тг</h3>
      </div>
    </div>
      </div>
    </div>
    <div v-else>...loading</div>
  </div>
</template>
