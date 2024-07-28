<template>
    <div>
        <!-- Enter ingredient field -->
        <input v-model="query" placeholder="Enter ingredient" @keyup.enter="searchRecipes" />
        <!-- Search button -->
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
