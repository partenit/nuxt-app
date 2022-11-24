<template>
  <div>
    <h1>Laravel Api with Nuxt 3 Fetch Api Data</h1>
    <ul v-for="category in categories" :key="category.id">
      <li>Id: {{ category.id }}</li>
      <li>Name: {{ category.name }}</li>
    </ul>
  </div>
</template>

<script setup>
import {useFetch} from "nuxt/app";

const response = await useFetch('https://test-shop.estater.biz/api/v1/categories')
const categories = response.data._rawValue.data
console.log(categories)

</script>

