<template>
  <div id="app">
    <header>
      <h1>Recipe Finder App</h1>
      <p>Discover delicious recipes and get cooking tips right at home!</p>
    </header>
    <!-- Component for entering recipe search queries -->
    <RecipeForm @search="fetchRecipes" />
    <!-- Component to display the list of recipes, and show a message if no recipes are found after a search -->
    <RecipeList :recipes="recipes" :searchExecuted="searchExecuted" />
  </div>
</template>

<script>
import RecipeForm from './components/RecipeForm.vue'; // Import the RecipeForm component for handling recipe searches
import RecipeList from './components/RecipeList.vue'; // Import the RecipeList component for displaying the list of recipes

export default {
  data() {
    return {
      recipes: [], // Array to store the recipes fetched from the API
      searchExecuted: false // Flag to track if a search has been executed
    };
  },
  components: {
    RecipeForm,
    RecipeList
  },
  methods: {
    // Method to fetch recipes from the API based on the search query
    async fetchRecipes(query) {
      const appId = 'dd48d7fe';
      const appKey = 'c084e1d8e2a291660ed3939970d911d9';
      // Fetch recipes from the Edamam API
      const response = await fetch(`https://api.edamam.com/search?q=${query}&app_id=${appId}&app_key=${appKey}`);
      const data = await response.json();
      // Save the list of recipes we got from the API
      this.recipes = data.hits;
      // Indicate that a search has been executed
      this.searchExecuted = true;
    }
  }
};
</script>

<style>
/* main app container */
#app {
  font-family: 'Arial', sans-serif;
  text-align: center;
  margin: 0 auto;
  max-width: 900px;
  background-color: #f8f9fa;
  padding: 20px;
  border-radius: 10px;
}

/* header */
header {
  position: relative;
  background: url('/public/images/background-image.jpeg') no-repeat center center;
  background-size: cover;
  height: 250px;
  padding: 20px;
  border-radius: 10px;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

header::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  border-radius: 10px;
  z-index: 1;
}

header>* {
  position: relative;
  z-index: 2;
}

/* h1 */
h1 {
  font-size: 2.5rem;
  margin: 0;
}

/* paragraph */
p {
  font-size: 1.2rem;
  margin-top: 10px;
}
</style>