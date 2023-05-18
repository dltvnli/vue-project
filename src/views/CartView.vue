<script setup>
    import cartMethods from '../utils/cart';
    import { ref, watch } from 'vue';
    import { onMounted } from 'vue';

    const cart = ref([]);

    const fetchCart = () => {
        cart.value = cartMethods.getCart();
    }

    const removeItem = (id) => {
        cartMethods.removeFromCartById(id);
        cart.value = cartMethods.getCart();
    }

    const clearCart = () => {
        cartMethods.clearCart();
        cart.value = cartMethods.getCart();
    }

    onMounted(async () => {
        fetchCart();
    })
</script>

<template>
    <div >
        <h1 class = " me-md-3 pt-3 px-3  px-md-5  text-center">Cart</h1>
        <div class="row row-cols-6">
        <div 
        class="card card-hover py-3 my-2 gx-5 text-center container-sm "
        style="width: 20%"
        v-for="item in cart"
         :key="item.id">
         <div>
         <RouterLink :to="'product/' + item.id">
            <img :src="item.image" class="card-img-top" :alt="item.title" />
          </RouterLink>
            <h3>{{ item.title }}</h3>
            <p class ="lead fw-normal text"> Price:{{ item.price }} тг</p>
            <div class = " me-md-3 pt-3 px-3  px-md-5 ">
            <button class="btn btn-outline-secondary " @click="removeItem(item.id)"  type="button ">Remove</button>
          </div>
        </div>
      </div>
    </div>
        <div v-if="cart.length === 0">
            <h3>Cart is empty</h3>
        </div>
        <div v-if="cart.length > 0">
            <h3 class=" me-md-3 pt-3 " >Total: {{ cartMethods.getCartTotal() }} тг </h3>
            <button @click="clearCart()" type="button" class="btn btn-secondary">Clear cart</button>
        </div>
    </div>
</template>