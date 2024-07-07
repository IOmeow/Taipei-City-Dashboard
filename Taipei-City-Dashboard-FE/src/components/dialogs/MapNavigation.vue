<!-- Developed by Taipei Urban Intelligence Center 2023-2024-->

<script setup>
import { ref, computed, onMounted } from "vue";
import { useMapStore } from "../../store/mapStore";
import { useDialogStore } from "../../store/dialogStore";
// import { useAuthStore } from "../../store/authStore";
import { useContentStore } from "../../store/contentStore";
import axios from '../../router/axios';

// import DialogContainer from "./DialogContainer.vue";
// import CustomCheckBox from "../utilities/forms/CustomCheckBox.vue";

const mapStore = useMapStore();
const contentStore = useContentStore();

// const dialogStore = useDialogStore();
// const authStore = useAuthStore();

const directions = ref(null);
let allCoordinates = [];

// export const useMapARStore = defineStore('mapAR', {
// 	state: () => ({
// 		allCoordinates: [],
// 		MAPTOKEN: import.meta.env.VITE_MAPBOXTOKEN,
// 		start: "",
// 		apiUrl: "",
// 		directions: null,

// 	}),
// 	actions: {
// 		initLocation(){
// 			this.start = mapStore.useLocation.longtitude + "," + mapStore.userLocation.latitude;
// 		},
// 		async getDirections(lon, lat, {commit}){
// 			this.end = String(lon) + "," + String(lat);
// 			apiUrl = 'https://api.mapbox.com/directions/v5/mapbox/walking/${this.start};${this.end}?alternatives=true&continue_straight=true&geometries=geojson&language=en&overview=full&steps=true&access_token=${this.MAPBOXTOKEN}`;'
// 			axios
// 				.get(apiURL)
// 				.then((res) => {
// 					if(res.status == 200){
// 						commit('setDirection', res.data)
// 					}
// 				})
// 				.catch((err) =>{
// 					console.log("Error fetching direction:" + err);
// 				})  
// 		}
// 	},
// 	mutations: {
// 		setDirection: (state, data) => state.directions = data
// 	}
// })

onMounted(()=>{
	mapStore.setCurrentLocation();
	contentStore.getAllParkingData();
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
