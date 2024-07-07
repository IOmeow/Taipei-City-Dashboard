<script setup>
import {onMounted} from 'vue';
import { useContentStore } from "../../store/contentStore";

const contentStore = useContentStore();

onMounted(()=>{
	contentStore.getAllParkingData();
})
</script>

<template>
	<div>
		{{ contentStore.parkingDatas }}
  	</div>
</template>