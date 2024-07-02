<template>
  <div>
   
    <ImageComponent />
    <SearchComponent @search="handleSearch" />
    <PopularProducts />
    <ServicesCard />
    <ProductsCard />
    <JobsCard />
  </div>
</template>

<script>

import ImageComponent from '@/components/ImageComponent.vue';
import SearchComponent from '@/components/SearchComponent.vue';
import PopularProducts from '@/components/PopularProducts.vue';
import ServicesCard from '@/components/ServicesCard.vue';
import ProductsCard from '@/components/ProductsCard.vue';
import JobsCard from '@/components/JobsCard.vue';

export default {
  name: 'HomeView',
  components: {
    
    ImageComponent,
    SearchComponent,
    PopularProducts,
    ServicesCard,
    ProductsCard,
    JobsCard
  },
  methods: {
    handleSearch(searchTerm) {
      // Implement your search functionality here
      console.log('Searching for:', searchTerm);
      // Example: Call a method to process search results or filter data
    },
},
}
</script>

<style scoped>
/* You can add your view-specific styles here */
</style>
