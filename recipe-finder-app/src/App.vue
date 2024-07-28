<template>
  <div id="app">
    <h1>Recipe Finder App</h1>
    <!-- Component for entering recipe search queries -->
    <RecipeForm @search="fetchRecipes" />
    <!-- Component for showing the list of recipes -->
    <RecipeList :recipes="recipes" />
  </div>
</template>

<script>
import RecipeForm from './components/RecipeForm.vue'; // Import the RecipeForm component for handling recipe searches
import RecipeList from './components/RecipeList.vue'; // Import the RecipeList component for displaying the list of recipes

export default {
  data() {
    return {
      // Array to store the recipes fetched from the API
      recipes: []
    };
  },
  components: {
    RecipeForm,
    RecipeList
  },
  methods: {
    // Method to fetch recipes from the API based on the search query
    async fetchRecipes(query) {
      const appId = process.env.VUE_APP_EDAMAM_APP_ID;
      const appKey = process.env.VUE_APP_EDAMAM_APP_KEY;
      // Fetch recipes from the Edamam API
      const response = await fetch(`https://api.edamam.com/search?q=${query}&app_id=${appId}&app_key=${appKey}`);
      const data = await response.json();
      // Save the list of recipes we got from the API
      this.recipes = data.hits;
    }
  }
};
</script>

<style>
/* Styling for the app */
#app {
  font-family: Arial, sans-serif;
  text-align: center;
  margin: 0 auto;
  max-width: 800px;
}

img {
  max-width: 100%;
  height: auto;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  margin-bottom: 20px;
}
</style>
