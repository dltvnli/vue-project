<script setup>
import Card from "../components/Card.vue";
import Pagination from "../components/Pagination.vue";
import Dropdown from "../components/Dropdown.vue";
</script>

<template>
  <div class="container">
    <h1>About Page</h1>
    <Dropdown title="sort" :items="['price asc', 'price desc']"/>
    <div class="row row-cols-4">
      <Card v-for="i in 9" :key="i" class="col m-3"/>
    </div>
    <Pagination />
  </div>
</template>