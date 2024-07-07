<script setup>
// import { onMounted } from 'vue';
// import '@ar-js-org/ar.js';
import MapNavigation from "../components/dialogs/MapNavigation.vue";

</script>

<template>
  <MapNavigation />
  <div style="height:max-content">
    <iframe
      src="https://iomeow.github.io/SteamSouthYo/"
      style="width: 100vw; height: 100vh; border: none;"
      allow="camera; geolocation"
    />
  </div>
</template>