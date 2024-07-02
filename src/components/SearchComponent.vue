<template>
    <div class="search-component">
      <input
        type="text"
        v-model="searchTerm"
        placeholder="Enter your search term..."
        @input="handleInput"
        class="search-input"
      />
      <button @click="search" class="search-button">Search</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'SearchComponent',
    data() {
      return {
        searchTerm: '', // Data property to hold the search term
      };
    },
    methods: {
      handleInput() {
        // Optional: Handle input changes dynamically if needed
      },
      search() {
        // Implement search functionality here
        // You can emit an event or call a method in parent component
        console.log('Searching for:', this.searchTerm);
        // Example: Emitting an event to notify parent component
        this.$emit('search', this.searchTerm);
      },
    },
  };
  </script>
  
  <style scoped>
  .search-component {
    margin-top: 20px; /* Adjust margin as needed */
    text-align: center; /* Center align the search box */
  }
  
  .search-input {
    padding: 0.5rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
    width: 300px; /* Adjust width as needed */
  }
  
  .search-button {
    margin-left: 0.5rem;
    padding: 0.5rem 1rem;
    font-size: 1rem;
    background-color: #1d242c; /* Example button color */
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .search-button:hover {
    background-color: #494b4d; /* Darker color on hover */
  }
  </style>
  