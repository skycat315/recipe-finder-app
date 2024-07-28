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
                <h3 class="recipe-name">{{ recipe.recipe.label }}</h3>
                <!-- Display recipe source -->
                <p class="recipe-source">{{ recipe.recipe.source }}</p>
                <!-- Display a link to view the full recipe -->
                <a class="recipe-link" :href="recipe.recipe.url" target="_blank">View Recipe</a>
            </li>
        </ul>
    </div>
    <!-- Display a message when no recipes are available -->
    <div v-else-if="searchExecuted">
        <p>No recipes found.</p>
    </div>
</template>

<script>
export default {
    props: {
        recipes: Array, // Array of recipes passed from parent component
        searchExecuted: Boolean // Receive the searchExecuted flag from the parent component
    }
};
</script>

<style>
/* recipe images */
img {
    max-width: 100%;
    height: auto;
    border-radius: 8px;
}

/* unordered list */
ul {
    list-style: none;
    padding: 0;
}

/* list items */
li {
    margin-bottom: 20px;
    padding: 15px;
    background: #ffffff;
    border-radius: 8px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}

/* recipe name */
h3.recipe-name {
    color: #333333;
    font-size: 1.5rem;
    margin: 10px 0;
    font-weight: bold;
}

/* recipe source */
p.recipe-source {
    color: #777777;
    font-size: 1rem;
    margin: 0 0 10px 0;
}

/* recipe link */
a.recipe-link {
    color: #007bff;
    text-decoration: none;
    font-weight: bold;
}

a.recipe-link:hover {
    text-decoration: underline;
}
</style>