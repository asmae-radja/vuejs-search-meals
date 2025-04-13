<template>
    <div class="bg-white shadow rounded-xl hover:scale-105 transition-all">
        <router-link :to="{ name: 'mealsDetails', params: { id: meal.idMeal } }">
            <img :src="meal.strMealThumb" class="w-full h-48 object-cover" />
        </router-link>
        <div class="p-3">
            <h3 class="font-bold">{{ meal.strMeal }}</h3>
            <p class="mb-4">
                Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et
                dolore magna aliqua.
            </p>
            <div class="flex items-center justify-between">
                <YouTubeButton :href=" meal.strYoutube">Youtube</YouTubeButton>
            </div>
        </div>
    </div>
</template>
<script setup>
import YouTubeButton from './YouTubeButton.vue';

const { meal } = defineProps({
    meal:{
        required: true,
        type: Object,
    },
});
</script>