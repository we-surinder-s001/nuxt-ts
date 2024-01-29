<template>
  <div class="container">
    <h1>Type Checking for API calls:</h1>
    <br/>
    <div v-if="is_loading">
      Loading Products...
    </div>
    <div v-else v-for="product in products_list" :key="product.id">
      {{ product.id }} - {{ product.title }}
    </div>
  </div>
</template>

<script setup lang="ts">
import {ref} from "vue";

const products_list = ref<Products[]>([]);
const is_loading = ref<boolean>(false);

type Products =
    {
      id: number;
      title: string;
      price: string;
      category: string;
      description: string;
      image: string;
    }


// try 1::
const get_products = async (): Promise<void> => {
  is_loading.value = true
  const res = await fetch("https://fakestoreapi.com/products");
  const resjson = await res.json();
  is_loading.value = false
  products_list.value = resjson;
};
get_products();


// try 2::
// const get_products = async (): Promise<void> => {
//   is_loading.value = true
//   const res = await $fetch("https://fakestoreapi.com/products");
//   is_loading.value = false;
//   products_list.value = res
// };

// try 3::
// const get_products = async (): Promise<void> => {
//   is_loading.value = true
//   const {data: products} = await useFetch('https://fakestoreapi.com/products');
//   is_loading.value = false
//   products_list.value = products.value
// }
// get_products();

// try 4::
// const {data: products} = await useAsyncData('products', (): Promise<Products[]> => $fetch('https://fakestoreapi.com/products'));
// products_list.value = products.value;
</script>

<style scoped>
.container {
  padding: 0.5rem 0.5rem;
}
</style>
