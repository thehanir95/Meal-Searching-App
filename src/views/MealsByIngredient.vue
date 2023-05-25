<template>
    <Meals :meals="meals"/>
</template>

<script setup>
import store from '../store';
import { onMounted } from 'vue';
import { computed } from '@vue/reactivity';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue'

const route = useRoute();
const meals = computed(() => store.state.mealsByIngredients)


onMounted(() =>{
    console.log( route.params)
    store.dispatch('searchMealsByIngredients', route.params.ingredient)
})
</script>