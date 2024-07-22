<template>
    <div class="ad-card">
      <div class="ad-content">
        <div class="image-container">
          <img :src="image" alt="Ad Image" class="ad-image" />
        </div>
        <div class="ad-details">
          <h2>{{ title }}</h2>
          <p class="price">₹{{ price }}</p>
          <p><strong>Location:</strong> {{ location }}</p>
          <p><strong>Condition:</strong> {{ condition }}</p>
          <p><strong>Warranty:</strong> {{ warranty }}</p>
          <div class="ad-description">
            <p>{{ description }}</p>
          </div>
          <div class="actions">
            <button class="buy-now-button">Buy Now</button>
          </div>
        </div>
      </div>
      <div class="message-to-seller">
        <h3>Contact Seller</h3>
        <textarea v-model="message" placeholder="Type your message..."></textarea>
        <div class="buttons">
          <button @click="sendMessage">Submit</button>
          <button @click="sendWhatsAppMessage">WhatsApp</button>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        image: 'https://via.placeholder.com/300x200.png?text=Ad+Image',
        title: 'Ad Title',
        price: 1314,
        location: 'Chennai',
        condition: 'New',
        warranty: 'No',
        description: 'This is a detailed description of the product being advertised. It includes key features, benefits, and other relevant information that potential buyers might find useful.',
        message: ''
      };
    },
    methods: {
      sendMessage() {
        // Handle sending message to the seller
        console.log('Message sent:', this.message);
      },
      sendWhatsAppMessage() {
        // Handle sending WhatsApp message
        const phoneNumber = '300-482952878';
        const url = `https://api.whatsapp.com/send?phone=${phoneNumber}&text=${encodeURIComponent(this.message)}`;
        window.open(url, '_blank');
      }
    }
  };
  </script>
  
  <style scoped>
  .ad-card {
    max-width: 900px;
    margin: 20px auto;
    padding: 20px;
    background-color: #fff;
    border-radius: 8px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    font-family: 'Arial', sans-serif;
    color: #333;
  }
  .ad-content {
    display: flex;
    flex-wrap: wrap;
    gap: 20px;
  }
  .image-container {
    flex: 1;
    text-align: center;
  }
  .ad-image {
    width: 100%;
    max-width: 400px;
    height: auto;
    border-radius: 8px;
  }
  .ad-details {
    flex: 2;
    text-align: left;
  }
  .ad-details h2 {
    margin-bottom: 10px;
    color: #333;
    font-size: 24px;
  }
  .ad-details .price {
    color: #b12704;
    font-size: 22px;
    margin-bottom: 5px;
  }
  .ad-details p {
    margin: 5px 0;
    color: #555;
  }
  .ad-description {
    margin: 20px 0;
  }
  .actions {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
  }
  .buy-now-button {
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 16px;
    background-color: #000;
    color: #fff;
    transition: background-color 0.3s;
  }
  .buy-now-button:hover {
    background-color: #333;
  }
  .message-to-seller {
    margin-top: 20px;
    padding-top: 20px;
    border-top: 1px solid #ddd;
  }
  .message-to-seller h3 {
    margin-bottom: 10px;
    color: #333;
  }
  .message-to-seller textarea {
    width: 100%;
    height: 80px;
    margin-bottom: 10px;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 14px;
    font-family: 'Arial', sans-serif;
  }
  .message-to-seller .buttons {
    display: flex;
    gap: 10px;
  }
  .message-to-seller button {
    background-color: #3498db;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    font-size: 14px;
    transition: background-color 0.3s;
  }
  .message-to-seller button:hover {
    background-color: #2980b9;
  }
  </style>
  