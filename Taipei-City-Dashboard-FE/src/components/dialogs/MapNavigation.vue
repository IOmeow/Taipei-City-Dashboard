<!-- Developed by Taipei Urban Intelligence Center 2023-2024-->

<script setup>
import { ref, computed, onMounted } from "vue";
import { useMapStore } from "../../store/mapStore";
import { useDialogStore } from "../../store/dialogStore";
// import { useAuthStore } from "../../store/authStore";
import axios from '../../router/axios';

// import DialogContainer from "./DialogContainer.vue";
// import CustomCheckBox from "../utilities/forms/CustomCheckBox.vue";

const mapStore = useMapStore();
const dialogStore = useDialogStore();
// const authStore = useAuthStore();

const directions = ref(null);
let allCoordinates = [];

async function getDirections(lon, lat) {
	const MAPBOXTOKEN = import.meta.env.VITE_MAPBOXTOKEN;
	const start = mapStore.userLocation.longitude + "," + mapStore.userLocation.latitude;
	const end = String(lon) + "," + String(lat);
	const url = `https://api.mapbox.com/directions/v5/mapbox/walking/${start};${end}?alternatives=true&continue_straight=true&geometries=geojson&language=en&overview=full&steps=true&access_token=${MAPBOXTOKEN}`;

	try {
		const response = await axios.get(url);
    	directions.value = response.data;
		directions.value.routes.forEach(route => {
			route.legs.forEach(leg => {
				leg.steps.forEach(step => {
					allCoordinates = allCoordinates.concat(step.geometry.coordinates);
				});
			});
		});
	} catch (error) {
		console.error('Error fetching directions:', error);
	}
}

onMounted(()=>{
	mapStore.setCurrentLocation();
})


</script>

<template>
  <div class="map-navigation">
    <h2>Map Navigation</h2>
    <button @click="getDirections(121.562367, 25.033490)">
      Get Directions
    </button>
    <div v-if="directions">
      <h2>Directions</h2>
      <pre>{{ allCoordinates }}</pre>
    </div>
  </div>
</template>


<style scoped lang="scss">
.map-navigation {
  width: 100%;

  h2 {
    margin-bottom: 1rem;
    font-size: var(--font-m);
  }

  button {
    padding: 0.5rem 1rem;
    background-color: var(--color-primary);
    border: none;
    border-radius: 4px;
    color: white;
    cursor: pointer;

    &:hover {
      background-color: var(--color-primary-dark);
    }
  }

  pre {
    background-color: #f5f5f5;
    padding: 1rem;
    border-radius: 4px;
    overflow-x: auto;
  }
}
</style>
