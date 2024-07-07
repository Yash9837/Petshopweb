<template>
  <div class="profile-container">
    
    <div class="user-details">
      <div class="user-header">
        <div class="avatar-placeholder" @click="editMode && triggerFileInput">
          <img v-if="user.photo" :src="user.photo" alt="User Photo" />
          <input type="file" ref="fileInput" @change="handleFileUpload" style="display: none;" />
        </div>
        <div class="user-info">
          <div class="user-info-header">
            <h2>{{ user.name }}</h2>
            <div class="button-group">
              <button class="edit-profile" @click="toggleEditMode">{{ editMode ? 'Save Profile' : 'Edit Profile' }}</button>
              <button class="messages-button" @click="goToMessages">Messages</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    
    <div class="ad-stats">
      <div class="stat">
        <h3>{{ stats.adsSold }}</h3>
        <p>AD SOLD</p>
      </div>
      <div class="stat">
        <h3>{{ stats.totalListings }}</h3>
        <p>TOTAL LISTINGS</p>
      </div>
      <div class="stat">
        <h3>{{ stats.inactiveAds }}</h3>
        <p>INACTIVE ADS</p>
      </div>
    </div>

    <!-- My Ads Section -->
    <div class="my-ads">
      <h3 @click="toggleAdsDropdown">My Ads <span>{{ adsDropdown ? '▲' : '▼' }}</span></h3>
      <ul v-if="adsDropdown">
        <li v-for="ad in userAds" :key="ad.id">{{ ad.title }}</li>
      </ul>
    </div>

    <!-- Manage Profile Section -->
    <div class="manage-profile">
      <h3>Manage Your Profile</h3>
      <form @submit.prevent="saveProfile" class="profile-form">
        <div class="profile-detail">
          <label for="name"><strong>Your name</strong></label>
          <div v-if="editMode">
            <input type="text" id="name" v-model="user.name" />
          </div>
          <div v-else>
            <p>{{ user.name }}</p>
          </div>
        </div>
        <div class="profile-detail">
          <label for="email"><strong>Email Address</strong></label>
          <div v-if="editMode">
            <input type="email" id="email" v-model="user.email" />
          </div>
          <div v-else>
            <p>{{ user.email }}</p>
          </div>
        </div>
        <div class="profile-detail">
          <label for="phone"><strong>Phone Number</strong></label>
          <div v-if="editMode">
            <input type="tel" id="phone" v-model="user.phone" />
          </div>
          <div v-else>
            <p>{{ user.phone }} <span class="verified">Verified</span></p>
          </div>
        </div>
        <div class="profile-detail">
          <label for="role"><strong>Location</strong></label>
          <div v-if="editMode">
            <input type="text" id="role" v-model="user.role" />
          </div>
          <div v-else>
            <p>{{ user.role }}</p>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserProfile',
  data() {
    return {
      user: {
        name: 'User-1',
        email: 'user1@example.com',
        phone: '1234567890',
        role: 'Chennai',
        photo: '',
      },
      stats: {
        adsSold: 0,
        totalListings: 0,
        inactiveAds: 0,
      },
      userAds: [
        { id: 1, title: '1' },
        { id: 2, title: '2' },
        { id: 3, title: '3' },
      ],
      adsDropdown: false,
      editMode: false,
    };
  },
  methods: {
    toggleEditMode() {
      if (this.editMode) {
        this.saveProfile();
      }
      this.editMode = !this.editMode;
    },
    saveProfile() {
      // Normally you would save the profile data here
      alert('Profile saved!');
    },
    triggerFileInput() {
      this.$refs.fileInput.click();
    },
    handleFileUpload(event) {
      const file = event.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onload = (e) => {
          this.user.photo = e.target.result;
        };
        reader.readAsDataURL(file);
      }
    },
    toggleAdsDropdown() {
      this.adsDropdown = !this.adsDropdown;
    },
    goToMessages() {
      // Redirect to messages or show messages dialog
      alert('Go to messages!');
    },
  },
};
</script>

<style scoped>
.profile-container {
  font-family: Arial, sans-serif;
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
}

.user-details {
  background-color: #f2f2f2;
  padding: 20px;
  border-radius: 5px;
  margin-bottom: 20px;
}

.user-header {
  display: flex;
  align-items: center;
}

.avatar-placeholder {
  width: 120px;
  height: 120px;
  background-color: #c4c4c4;
  border-radius: 50%;
  margin-right: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}

.avatar-placeholder img {
  width: 100%;
  height: 100%;
  border-radius: 50%;
}

.user-info {
  flex: 1;
}

.user-info-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.user-info h2 {
  margin: 0;
  font-size: 24px;
  color: #4a4a4a;
}

.button-group {
  display: flex;
  gap: 10px;
}

.edit-profile, .messages-button {
  background-color: #3d3d3d;
  color: white;
  border: none;
  padding: 10px;
  cursor: pointer;
  border-radius: 5px;
}

.edit-profile:hover, .messages-button:hover {
  background-color: #1e1e1e;
}

.ad-stats {
  display: flex;
  justify-content: space-between;
  margin-bottom: 20px;
}

.stat {
  background-color: #e7e7e7;
  padding: 10px 20px;
  text-align: center;
  border-radius: 5px;
  flex: 1;
  margin-right: 10px;
}

.stat:last-child {
  margin-right: 0;
}

.stat h3 {
  margin: 0;
  color: #333;
}

.my-ads {
  background-color: #ffffff;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  margin-bottom: 20px;
  cursor: pointer;
}

.my-ads h3 {
  margin: 0;
  color: #333;
}

.my-ads ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
}

.my-ads ul li {
  padding: 5px 0;
  color: #666;
}

.manage-profile {
  background-color: #ffffff;
  padding: 20px;
  border-radius: 5px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

.manage-profile h3 {
  margin-top: 0;
  color: #333;
}

.profile-form {
  display: flex;
  flex-direction: column;
}

.profile-detail {
  display: flex;
  margin: 10px 0;
  align-items: center;
}

.profile-detail label {
  width: 150px;
  margin-right: 20px;
}

.profile-detail input {
  flex: 1;
  padding: 5px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.verified {
  color: green;
}

@media (max-width: 600px) {
  .avatar-placeholder {
    width: 100px;
    height: 100px;
  }

  .button-group {
    flex-direction: column;
    align-items: center;
  }

  .stat {
    flex: 1 1 100%;
  }
}

@media (max-width: 400px) {
  .avatar-placeholder {
    width: 80px;
    height: 80px;
  }
}
</style>
