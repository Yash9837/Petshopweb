<template>
  <div class="image-component">
    <img src="../assets/petshop1.jpg" alt="hh" />
  </div>
</template>

<script>
export default {
  name: 'ImageComponent',
};
</script>

<style scoped>
.image-component {
  margin-top: 20px;
   /* Adjust margin as needed */
  text-align: center; /* Center align the image */
  max-width: auto; /* Ensure the image component does not exceed its container */
  display: flex;
  justify-content: center;
  align-items: center;
}

.image-component img {
  width: 60%; /* Make the image slightly smaller */
  height: 40%; /* Maintain aspect ratio */
  max-width: 100%; /* Ensure the image does not exceed its container */
  border: 2px solid #000; /* Add a border */
  border-radius: 10px; /* Make the corners slightly curved */
  padding: 5px; /* Add some padding around the image */
}
</style>
