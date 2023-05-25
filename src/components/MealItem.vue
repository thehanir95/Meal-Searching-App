<template>
    <div class="bg-white shadow rounded-xl">

    <router-link :to="{name: 'mealDetails', params: {id: meal.idMeal}}">
        <img :src="meal.strMealThumb" alt="strMeal" class="rounded-t-xl w-full h-48 object-cover">
    </router-link>
    <div class="p-3">
        <h3 class="font-bold">{{ meal.strMeal }}</h3>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab, cum. Quas ipsam voluptatum numquam, cupiditate veniam commodi distinctio nobis eveniet illo vel sapiente alias nam quaerat labore porro! Corrupti, praesentium!</p>
        <div class="flex items-center justify-between" >
        <YouTubeBtn :href="meal.strYoutube">YouTube</YouTubeBtn>   
        </div>
    </div>
    </div>
</template>

<script setup>
import YouTubeBtn from '../components/YouTubeBtn.vue'
const { meal } = defineProps({
    meal: {
        required: true,
        type: Object
    }
})
</script>