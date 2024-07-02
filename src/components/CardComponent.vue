<template>
    <div class="card">
      <div class="card-image-container">
        <img :src="imageSrc" alt="Product Image" class="card-image" />
        <button class="image-button">
          <i class="fas fa-heart"></i>
        </button>
      </div>
      <div class="card-content">
        <h3 class="product-name">{{ productName }}</h3>
        <p class="category">{{ category }}</p>
        <p class="price">{{ price }}</p>
        <p class="rating"><i class="fas fa-star"></i> {{ rating }}</p>
        <button class="buy-button">Buy Now</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CardComponent',
    props: {
      imageSrc: {
        type: String,
        required: true,
      },
      productName: {
        type: String,
        required: true,
      },
      category: {
        type: String,
        required: true,
      },
      price: {
        type: String,
        required: true,
      },
      rating: {
        type: String,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .card {
    border: 1px solid #ccc;
    border-radius: 8px;
    overflow: hidden;
    width: 100%;
    max-width: 300px;
    margin: 1rem;
  }
  
  .card-image-container {
    position: relative;
    width: 100%;
    padding-top: 75%; /* 4:3 Aspect Ratio */
  }
  
  .card-image {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .image-button {
    position: absolute;
    top: 10px;
    right: 10px;
    padding: 0.5rem;
    background-color: rgba(255, 255, 255, 0.8);
    border: none;
    border-radius: 50%;
    cursor: pointer;
  }
  
  .image-button i {
    color: black;
    font-size: 1.2rem;
  }
  
  .card-content {
    padding: 1rem;
  }
  
  .product-name {
    font-size: 1.2rem;
    font-weight: bold;
  }
  
  .category {
    font-size: 1rem;
    color: #777;
  }
  
  .price {
    font-size: 1.2rem;
    color: #000;
    font-weight: bold;
  }
  
  .rating {
    font-size: 1rem;
    color: #ff9900;
  }
  
  .buy-button {
    margin-top: 0.5rem;
    padding: 0.5rem 1rem;
    background-color: #000;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .buy-button:hover {
    background-color: #333;
  }
  </style>
  