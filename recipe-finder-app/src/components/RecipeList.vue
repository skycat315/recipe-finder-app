<template>
    <!-- Display recipes if there are any -->
    <div v-if="recipes && recipes.length">
        <h2>Recipes</h2>
        <ul>
            <!-- Iterate over the recipes array and display each recipe -->
            <li v-for="recipe in recipes" :key="recipe.recipe.uri">
                <!-- Display recipe image -->
                <img :src="recipe.recipe.image" :alt="recipe.recipe.label" />
                <!-- Display recipe name -->
                <h3>{{ recipe.recipe.label }}</h3>
                <!-- Display recipe source -->
                <p>{{ recipe.recipe.source }}</p>
                <!-- Display a link to view the full recipe -->
                <a :href="recipe.recipe.url" target="_blank">View Recipe</a>
            </li>
        </ul>
    </div>
    <!-- Display a message when no recipes are available -->
    <div v-else>
        <p>No recipes found.</p>
    </div>
</template>

<script>
export default {
    props: {
        // Array of recipes passed from parent component
        recipes: Array
    }
};
</script>
