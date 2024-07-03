<template>
    <div class="post-ad-form">
      <h1>Post Ad</h1>
      <div class="steps">
        <span :class="{ active: step === 1 }">Step 1<br />Ad Information</span>
        <span :class="{ active: step === 2 }">Step 2<br />Ad Details</span>
        <span :class="{ active: step === 3 }">Step 3<br />User Information</span>
      </div>
      <form @submit.prevent="submitForm">
        <div v-if="step === 1">
          <div class="form-group">
            <label for="title">Title *</label>
            <input id="title" type="text" v-model="form.title" required />
          </div>
          <div class="form-group">
            <label for="category">Category *</label>
            <select id="category" v-model="form.category" required>
              <option disabled value="">Select suitable category for your ad</option>
              <option value="Animals/Pets">Animals/Pets</option>
              <option value="Electronics">Electronics</option>
              <option value="Vehicles">Vehicles</option>
            </select>
          </div>
          <div class="form-group" v-if="form.category === 'Animals/Pets'">
            <label for="subcategory">Subcategory *</label>
            <select id="subcategory" v-model="form.subcategory" required>
              <option disabled value="">Select suitable subcategory for your ad</option>
              <option value="Dogs">Dogs</option>
              <option value="Cats">Cats</option>
              <option value="Birds">Birds</option>
            </select>
          </div>
        </div>
        <div v-if="step === 2">
          <div class="form-group">
            <label for="price">Price *</label>
            <input id="price" type="number" v-model="form.price" required />
          </div>
          <div class="form-group">
            <label for="description">Description *</label>
            <textarea id="description" v-model="form.description" required></textarea>
          </div>
          <div class="form-group">
            <label for="photos">Photos *</label>
            <input id="photos" type="file" @change="handleFileUpload" multiple required />
          </div>
        </div>
        <div v-if="step === 3">
          <div class="form-group">
            <label for="name">Name *</label>
            <input id="name" type="text" v-model="form.name" required />
          </div>
          <div class="form-group">
            <label for="contact">Contact No *</label>
            <input id="contact" type="tel" v-model="form.contact" required />
          </div>
          <div class="form-group">
            <label for="state">State *</label>
            <select id="state" v-model="form.state" @change="fetchCities" required>
              <option disabled value="">Select your state</option>
              <option v-for="state in states" :key="state" :value="state">{{ state }}</option>
            </select>
          </div>
          <div class="form-group" v-if="form.state">
            <label for="city">City *</label>
            <select id="city" v-model="form.city" required>
              <option disabled value="">Select your city</option>
              <option v-for="city in cities" :key="city" :value="city">{{ city }}</option>
            </select>
          </div>
          <div class="form-group">
            <label for="address">Address *</label>
            <textarea id="address" v-model="form.address" required></textarea>
          </div>
          <div class="form-group">
            <input id="terms" type="checkbox" v-model="form.terms" required />
            <label for="terms">I accept the terms and conditions *</label>
          </div>
        </div>
        <div class="buttons">
          <button type="button" @click="prevStep" v-if="step > 1">Previous</button>
          <button type="button" @click="nextStep" v-if="step < 3">Next</button>
          <button type="submit" v-if="step === 3">Submit</button>
        </div>
      </form>
    </div>
  </template>
<script>
export default {
  data() {
    return {
      step: 1,
      form: {
        title: '',
        category: '',
        subcategory: '',
        price: '',
        description: '',
        photos: [],
        name: '',
        contact: '',
        state: '',
        city: '',
        address: '',
        terms: false
      },
      states: ['State1', 'State2', 'State3'], // backend
      cities: []
    }
  },
  methods: {
    nextStep() {
      if (this.step < 3) this.step++
    },
    prevStep() {
      if (this.step > 1) this.step--
    },
    handleFileUpload(event) {
      this.form.photos = Array.from(event.target.files)
    },
    fetchCities() {  //backend
      
      if (this.form.state === 'State1') {
        this.cities = ['City1-1', 'City1-2']
      } else if (this.form.state === 'State2') {
        this.cities = ['City2-1', 'City2-2']
      } else if (this.form.state === 'State3') {
        this.cities = ['City3-1', 'City3-2']
      }
    },
    submitForm() {
      
      console.log(this.form)
    }
  }
}
</script>
<style scoped>
.post-ad-form {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  background-color: #fff;
}

h1 {
  font-size: 24px;
  margin-bottom: 20px;
  text-align: center;
}

.steps {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.steps span {
  flex: 1;
  text-align: center;
  padding: 10px;
  border-bottom: 2px solid #e0e0e0;
  cursor: pointer;
}

.steps span.active {
  font-weight: bold;
  color: #2c3e50;
  border-bottom: 2px solid #2c3e50;
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}

input,
select,
textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  box-sizing: border-box;
}

textarea {
  resize: vertical;
  min-height: 100px;
}

.buttons {
  display: flex;
  justify-content: space-between;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 4px;
  background-color: #2c3e50;
  color: #fff;
  cursor: pointer;
}

button:hover {
  background-color: #34495e;
}

input[type="checkbox"] {
  margin-right: 10px;
}
</style>
