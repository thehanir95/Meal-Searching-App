<template>
    <div class="p-8">
        <input type="text" 
        class="rounded border-2 border-gray-200 w-full" 
        v-model="keyword"
        placeholder="Search from Meals"
        @change="searchMeals"
        />
    </div>
{{ meal }}
    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 p-8">
       <div v-for="meal in meals" :key="meal.idMeal" class="bg-white shadow rounded-xl">

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
    </div>
</template>

<script setup>
import { ref } from 'vue';
import { computed, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import YouTubeBtn from '../components/YouTubeBtn.vue'
 
import store from '../store';

const route = useRoute();
const keyword = ref('');
const meals = computed(() => store.state.searchedMeals);

function searchMeals() {
    store.dispatch('searchMeals', keyword.value)
}

onMounted(() => {
    keyword.value = route.params.name
    if (keyword.value) {
        searchMeals()
    }
})

</script>