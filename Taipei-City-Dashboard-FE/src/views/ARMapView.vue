<script setup>
import { onMounted } from 'vue';
import '@ar-js-org/ar.js';
import MapNavigation from "../components/dialogs/MapNavigation.vue";

const loadARScripts = () => {
	const addScript = (src) => {
		const script = document.createElement('script');
		script.src = src;
		document.head.appendChild(script);
	};

	addScript("https://cdn.jsdelivr.net/gh/aframevr/aframe@1c2407b26c61958baa93967b5412487cd94b290b/dist/aframe-master.min.js");
	addScript("https://unpkg.com/aframe-look-at-component@0.8.0/dist/aframe-look-at-component.min.js");
	addScript("https://raw.githack.com/cmcfadden/AR.js/master/aframe/build/aframe-ar.js");

	// Set AR.js Base URL
	window.THREEx = { ArToolkitContext: { baseURL: 'https://raw.githack.com/jeromeetienne/ar.js/master/three.js/' } };
};

onMounted(loadARScripts);
</script>

<template>
  <div style="margin: 0; overflow: hidden;">
    <!-- <a-scene
      vr-mode-ui="enabled: false"
      embedded
      arjs="sourceType: webcam; debugUIEnabled: false;"
    >
      <a-text
        value="parking lot"
        gps-entity-place="latitude: 24.821606723437057; longitude: 121.02627622688387;"
        position="0 2 0"
        rotation="0 0 0"
        font="mozillavr"
        color="#e43e31"
        look-at="#camera"
        side="double"
        align="center"
        scale="10 10 10"
      />
      <a-text
        value="Taipei City Dashboard"
        gps-entity-place="latitude: 24.821524831160087; longitude: 121.02589976027265;"
        position="0 2 0"
        rotation="0 0 0"
        font="mozillavr"
        color="white"
        look-at="#camera"
        side="double"
        align="center"
        scale="10 10 10"
      />
      <a-text
        value="milksha"
        gps-entity-place="latitude: 24.820801917677194; longitude: 121.02595576357018;"
        position="0 2 0"
        rotation="0 0 0"
        font="mozillavr"
        color="#e43e31"
        look-at="#camera"
        side="double"
        align="center"
        scale="10 10 10"
      />
      <a-camera
        id="camera"
        gps-camera="simulateLatitude: 24.821413416378828; simulateLongitude: 121.02623662258087;"
        rotation-reader
        far="900000"
      />
    </a-scene> -->
    <MapNavigation />
  </div>
</template>