<template>
  <div class="auth-container">
    <div class="signup-section">
      <signup-form />
    </div>
    <div class="poster-section">
      <div class="poster">
        <!-- Display different logos based on screen size -->
        <b-card-img src="/logo/deebate-logo-light.png" alt="Light Logo" class="logo light-logo" />
        <b-card-img src="/logo/deebate-logo-dark.png" alt="Dark Logo" class="logo dark-logo" />
        <b-card-text class="slogan m-0">
          <h4 class="fw-bold m-0">Deebate</h4>
          <p class="m-0 removable .rubik-text fw-lighter">Stand for your belief!</p>
        </b-card-text>
      </div>
    </div>
  </div>
</template>

<script>
import SignupForm from "@/components/authentication/SignupForm.vue";

export default {
  name: "signup",
  components: { SignupForm }
};
</script>

<style>
/* Set full height for html and body */
html, body {
  height: 100%;
  margin: 0;
}

.auth-container {
  display: flex;
  flex-direction: row;
  height: 100vh;
  justify-content: center;
  align-items: center;
}

.signup-section, .poster-section {
  width: 100%;
  height: 100%;
  justify-self: center;
}

.poster-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: #007769;
}

.poster {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
  gap: 5px;
}

.logo {
  max-width: 84px;
}

.slogan {
  color: white;
  text-align: center;
}

/* Initially, hide the dark logo and show the light logo */
.light-logo {
  display: block;
}

.dark-logo {
  display: none;
}

/* Media query for smaller screens */
@media (max-width: 768px) {
  .auth-container {
    flex-direction: column; /* Stack the items vertically */
  }

  .signup-section, .poster-section {
    width: 100%; /* Make both sections take up the full width */
    height: fit-content; /* Adjust height to content */
  }

  .poster-section {
    order: -1; /* Move poster section above login form */
    background-color: transparent; /* Remove dark background on small screens */
  }

  /* On smaller screens, hide the light logo and show the dark logo */
  .light-logo {
    display: none;
  }

  .dark-logo {
    display: block;
  }

  .slogan {
    color: #007769;
    text-align: center;
  }

  .removable {
    display: none;
  }
}
</style>
