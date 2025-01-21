<template>
    <nav id="navbar">
      <div class="logo">
        <a href="#home">Ricardo Méndez Cavalieri</a>
      </div>
      <ul class="main-nav" :class="{ 'mobile-nav': isMobileMenuOpen }">
        <li><a href="#github">GitHub</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
      <div class="menu-toggle" @click="toggleMobileMenu">
        <!-- Hamburger Icon -->
        <span></span>
        <span></span>
        <span></span>
      </div>
    </nav>
  </template>
  
  <script>
  export default {
    name: "NavbarComponent",
    data() {
      return {
        isMobileMenuOpen: false, // Tracks whether the mobile menu is open
      };
    },
    methods: {
      toggleMobileMenu() {
        this.isMobileMenuOpen = !this.isMobileMenuOpen;
      },
    },
  };
  </script>
  
  <style scoped>
/* Navbar styles */
#navbar {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  background: rgba(255, 255, 255, 0.9);
  color: #000000;
  border-bottom: 1px solid #ddd;
  z-index: 1000;
  padding: 10px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  box-sizing: border-box;
  height: 80px;
}

/* Logo styles */
.logo {
  flex-shrink: 0; /* Prevent the logo from shrinking */
}

.logo a {
  font-size: 2.5rem;
  color: #000000;
  text-decoration: none;
  white-space: nowrap; /* Prevent the title from wrapping */
}

/* Main navigation (desktop view) */
ul.main-nav {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  gap: 50px;
  flex-shrink: 1; /* Allow nav links to adjust for smaller screens */
}

.main-nav a {
  text-decoration: none;
  color: #000000;
  font-size: 1.5rem;
  font-weight: 500;
  display: block;
}

.main-nav a:hover {
  color: #718daa;
}

/* Hamburger menu toggle (hidden by default for large screens) */
.menu-toggle {
  display: none;
  flex-direction: column;
  justify-content: space-around;
  height: 24px;
  width: 30px;
  cursor: pointer;
}

.menu-toggle span {
  display: block;
  height: 3px;
  width: 100%;
  background: #000000;
  border-radius: 2px;
}

/* Responsive styles */
@media (max-width: 1000px) {
  #navbar {
    justify-content: space-between;
  }

  ul.main-nav {
    display: none;
    flex-direction: column;
    position: absolute;
    top: 80px; /* Below the navbar */
    right: 0;
    background: rgba(255, 255, 255, 0.95);
    width: 100%;
    padding: 20px 0;
    box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.1);
    gap: 20px;
    align-items: center;
    z-index: 999;
  }

  ul.main-nav.mobile-nav {
    display: flex;
  }

  .menu-toggle {
    display: flex;
  }

  .main-nav a {
    font-size: 1.2rem;
  }

}
</style>

  