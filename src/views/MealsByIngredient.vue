<template>
    <div class="flex flex-col p-8">
        <input type="text" v-model="ingredient" class="rounded border-2  border-gray-200 w-full"
            placeholder="Search for Meals with ingredient" @change="MealsByIngredient">
    </div>
    <div class="grid grid-cols-1 md:grid-cols-3 gap-5 px-8">
        <MealItem v-for="meal of meals" :key="meal.idMeal" :meal="meal"/>      
    </div>
</template>

<script setup>
import { computed, onMounted, ref, watch } from 'vue';
import store from '../store';
import { useRoute } from 'vue-router';
import MealItem from '../components/MealItem.vue';

const route = useRoute();
const ingredient = ref('');
const meals = computed(() => store.state.mealsByIngredient);

function MealsByIngredient() {
    console.log(ingredient.value)
    store.dispatch('searchMealsByIngredient', ingredient.value);
}


onMounted(() => {
   ingredient.value = route.params.ingredient;
    if(ingredient.value){
        MealsByIngredient()
    }
});
</script>