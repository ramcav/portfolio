<template>
    <div>
      <!-- Navbar -->
      <NavbarComponent />

      <!-- Horse Animation -->
      <HorseComponent />
    </div>
  </template>
  
  <script>
  import HorseComponent from "./HorseComponent.vue";
  import NavbarComponent from "./NavBarComponent.vue";
  
  export default {
    name: "MainComponent",
    components: {
      HorseComponent,
      NavbarComponent,
    },
  };
  </script>