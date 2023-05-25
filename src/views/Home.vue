<template>
    <div class="p-8 flex flex-col items-center">
        <h1 class="font-bold text-yellow-400 text-7xl pb-10">Search your Tasty</h1>
        <div class="flex justify-center w-2/4">
            <img src="https://cdn.store-assets.com/s/190466/i/10515970.jpeg" alt="front-img" class="rounded-full shadow-sm">
        </div>
    </div>
</template>

<script setup>
import { computed, onMounted, ref } from 'vue';
import store from '../store';
import axiosClient from '../axiosClient.js'

const ingredients = ref([])

onMounted(async () => {
    const response = await axiosClient.get('/list.php?i=list')
    console.log(response.data)
    ingredients.value = response.data
})
</script>