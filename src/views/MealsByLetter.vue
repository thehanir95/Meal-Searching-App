<template>
    <div class="flex justify-center mt-2">
        <div class="bg-white rounded-md w-fit p-3">
            <div class="flex justify-center gap-2">
                <router-link :to="{name: 'byLetter', params: {letter}}" v-for="letter of letters" :key="letter">
                {{ letter }}
                </router-link>
            </div>
        </div>
    </div>
    

    <Meals :meals="meals"/>
</template>

<script setup>
import store from '../store';
import { onMounted, watch } from 'vue';
import { computed } from '@vue/reactivity';
import { useRoute } from 'vue-router';
import Meals from '../components/Meals.vue'

const route = useRoute();
const letters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split("");
const meals = computed(() => store.state.mealsByLetter)

watch(route, () =>{
    store.dispatch('searchMealsByLetter', route.params.letter)
})

onMounted(() =>{
    store.dispatch('searchMealsByLetter', route.params.letter)
})
</script>