<template>
  <div class="main-container-menu primary-color text-white p-3 rounded-4"
       style="min-width: 210px;">
    <!-- Logo Section -->
    <div class="text-center logo-holder">
      <img :src="logoSrc" alt="Deebate Logo" class="logo img-fluid"/>
      <div>
        <h1 class="removable-text mb-0">Deebate</h1>
        <p class="removable-text">Stand for your belief!</p>
      </div>
    </div>

    <!-- Navigation Section -->
    <nav class="navigation-section flex-column justify-content-center">
      <ul class="text-start button-list">
        <li class="nav-item">
          <router-link to="/" class="nav-link text-white px-4" active-class="active">
            <i class="bi bi-house-fill"></i> <span class="removable-text">Home</span>
          </router-link>
        </li>
        <li class="nav-item">
          <router-link to="/profile" class="nav-link text-white px-4" active-class="active">
            <i class="bi-person-fill"></i> <span class="removable-text">Profile</span>
          </router-link>
        </li>
      </ul>
    </nav>

    <!-- Logout Button -->
    <button class="btn logout px-4" style="font-weight: 800" @click="logout">
      <i class="bi bi-door-open-fill removable-icon text-white"></i><span class="removable-text">Log out</span>
    </button>
  </div>
</template>


<script>
import logoSrc from '/logo/deebate-logo-light.png';
import 'bootstrap-icons/font/bootstrap-icons.css';

export default {
  name: 'MenuBar',
  data() {
    return {
      logoSrc
    };
  },
  methods: {
    logout() {
      localStorage.clear();
      this.$router.push('/login');
    }
  }
};
</script>


<style scoped>

/* Styling for the main container */
.main-container-menu {
  display: flex;
  flex-direction: column;
  min-width: 200px;
  min-height: 100%;
}

/* Styling for the primary color */
.primary-color {
  background-color: #007769;
}

/* Styling for the logo */
.logo {
  width: 70px;
  height: 70px;
}

/* Styling for the title */
h1 {
  font-size: 1.5em;
  font-weight: 800;
}

/* Styling for the paragraph */
p {
  font-size: 0.9em;
  margin: 0;
}

/* Styling for the navigation bar */
nav ul {
  list-style-type: none;
  padding: 0;
  font-weight: 600;
}

/* Styling for the navigation links */
.nav-link {
  color: white;
  text-decoration: none;
  border-radius: 15px;
  padding: 10px;
  transition: background-color 0.3s ease;
}

/* Ensures the active link is styled correctly */
.nav-link.active {
  background-color: #16B771;
  color: white;
}

/* Hover styling, only applied when the link is not active */
.nav-link:hover:not(.active) {
  background-color: rgba(22, 183, 113, 0.17);
}

/* Styling for the logout button */
.logout {
  background-color: #bb4545;
  color: white;
  border: none;
  padding: 12px;
  border-radius: 15px;
  cursor: pointer;
  transition: background-color 0.3s ease;
  margin-top: auto;
}

/* Hover styling for the logout button */
.logout:hover {
  background-color: #a13c3c;
}

.logo-holder {
  display: flex;
  flex-direction: column;
  align-items: center;
  row-gap: 15px;
  margin-bottom: 30px;
  margin-top: 20px;
}

/* Styling for the button list */
.button-list {
  display: flex;
  flex-direction: column;
  row-gap: 10px;
}

/* Styling for the removable text */
.removable-icon {
  display: none;
}

/* Styling for the logo holder */
.navigation-section {
  display: flex;
  flex-direction: column;
  row-gap: 10px;
  padding: 10px 0;
}


/* Responsive Styling */
@media (max-width: 992px) {
  .main-container-menu {
    position: sticky;
    top: 0;
    display: flex;
    flex-direction: row;
    max-height: fit-content;
    justify-content: space-between;
    align-items: center;
  }

  .removable-text {
    display: none;
  }

  .button-list {
    display: flex;
    flex-direction: row;
    column-gap: 10px;
    height: fit-content;
    margin-bottom: 0;
  }

  .logo {
    width: 40px;
    height: 40px;
  }

  .logo-holder {
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 5px;
    height: fit-content;
    margin-bottom: 0;
    margin-top: 0;
  }

  .navigation-section {
    flex-direction: row;
    column-gap: 10px;
    padding: 0;
  }

  .logout {
    margin: 0;
    height: fit-content;
    padding: 10px
  }

  .removable-icon {
    display: block;
  }

}

</style>

