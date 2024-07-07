<template>
  <div id="app">
    <nav class="navbar" role="navigation" aria-label="main navigation">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item">
          <img src="/src/assets/logo.png" alt="Petify" class="logo-image" />
          <!-- <span class="navbar-title">Petify</span> -->
        </router-link>
      </div>

      <div class="navbar-menu">
        <div class="navbar-end">
          <router-link to="/notifications" class="navbar-item">
            <i class="fas fa-bell"></i>
            <span class="notification-badge">4</span>
          </router-link>
          <router-link to="/chats" class="navbar-item">
            <i class="fas fa-comments"></i>
            <span class="notification-badge">4</span>
          </router-link>
          <router-link to="/favorites" class="navbar-item">
            <i class="fas fa-heart"></i>
            <span class="notification-badge">2</span>
          </router-link>
          <router-link to="/Profile" class="navbar-item">
            <i class="fas fa-user"></i>
          </router-link>
          <router-link to="/PostAd" class="navbar-item post-button">
            Post <i class="fas fa-plus"></i>
          </router-link>
        </div>
      </div>
    </nav>

    <router-view />
  </div>
</template>

<script>
export default {
  name: 'App',
};
</script>

<style scoped>
.navbar {
  background-color: #ffffff; /* Example background color */
  padding: 1rem;
  font-size: 1.2rem;
  border-bottom: 1px solid #eaeaea;
}

.navbar-brand {
  display: flex;
  align-items: center;
}

.logo-image {
  max-height: 2rem; /* Adjust based on your logo size */
}

.navbar-title {
  font-size: 1.5rem;
  font-weight: bold;
  margin-left: 0.5rem;
  color: #000;
}

.navbar-item {
  color: #000; /* Text color */
  margin-right: 1rem;
  position: relative;
}

.navbar-item i {
  font-size: 1.5rem; /* Icon size */
}

.navbar-item:hover {
  text-decoration: none;
  color: #555; /* Hover color */
}

.notification-badge {
  position: absolute;
  top: -5px;
  right: -5px;
  background-color: red;
  color: white;
  border-radius: 50%;
  padding: 0.2rem 0.4rem;
  font-size: 0.8rem;
}

.post-button {
  display: flex;
  align-items: center;
  background-color: #000;
  color: #fff;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 1rem;
}

.post-button i {
  margin-left: 0.5rem;
}

.navbar-menu {
  display: flex;
  justify-content: flex-end;
  align-items: center;
}

.navbar-end {
  display: flex;
  align-items: center;
}
</style>
