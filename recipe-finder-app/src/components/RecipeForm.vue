<template>
    <div>
        <!-- Input field for entering ingredient; triggers search on Enter key -->
        <input v-model="query" placeholder="Enter ingredient" @keyup.enter="searchRecipes" type="text" />
        <!-- Button to trigger the search functionality -->
        <button @click="searchRecipes">Search</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            // Data property to bind to input field
            query: ''
        };
    },
    methods: {
        // Emit a search event with the current query
        searchRecipes() {
            this.$emit('search', this.query);
        }
    }
};
</script>

<style>
/* search field */
input[type="text"] {
    font-size: 1.2rem;
    padding: 10px;
    margin: 0 10px;
    border: 2px solid #8e735b;
    border-radius: 5px;
    width: calc(100% - 22px);
    max-width: 500px;
    margin-bottom: 10px;
    box-sizing: border-box;
}

/* search button */
button {
    font-size: 1.2rem;
    padding: 10px 20px;
    background-color: #8e735b;
    color: #ffffff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    transition: background-color 0.3s, box-shadow 0.3s;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

button:hover {
    background-color: #6f4f28;
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.3);
}
</style>