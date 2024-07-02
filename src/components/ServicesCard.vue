<template>
    <div>
      <h2 class="section-title">Services</h2>
      <div class="card-row">
        <CardComponent
          v-for="(card, index) in cards"
          :key="index"
          :imageSrc="card.imageSrc"
          :productName="card.productName"
          :category="card.category"
          :price="card.price"
          :rating="card.rating"
        />
      </div>
    </div>
  </template>
  
  <script>
  import CardComponent from './CardComponent.vue';
  
  export default {
    name: 'ServicesCard',
    components: {
      CardComponent,
    },
    data() {
      return {
        cards: [
          {
            imageSrc: './src/assets/Rectangle5.png',
            productName: 'Product Name',
            category: 'Category',
            price: '$129',
            rating: '4.6',
          },
          {
            imageSrc: './src/assets/product2.jpg',
            productName: 'Product Name',
            category: 'Category',
            price: '$129',
            rating: '4.6',
          },
          {
            imageSrc: './src/assets/product3.jpg',
            productName: 'Product Name',
            category: 'Category',
            price: '$129',
            rating: '4.6',
          },
          {
            imageSrc: './src/assets/product4.jpg',
            productName: 'Product Name',
            category: 'Category',
            price: '$129',
            rating: '4.6',
          },
        ],
      };
    },
  };
  </script>
  
  <style scoped>
  .section-title {
    text-align: center;
    font-size: 1.5rem;
    margin: 2rem 0;
  }
  
  .card-row {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
  }
  </style>
  