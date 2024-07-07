<template>
  <head>
    <meta charset="utf-8">
    <meta
      http-equiv="X-UA-Compatible"
      content="IE=edge"
    >
    <title>AR.JS Demo with Location Simulation and Altitude</title>
    <script src="https://cdn.jsdelivr.net/gh/aframevr/aframe@1c2407b26c61958baa93967b5412487cd94b290b/dist/aframe-master.min.js" />
    <script src="https://unpkg.com/aframe-look-at-component@0.8.0/dist/aframe-look-at-component.min.js" />
    <script src="https://raw.githack.com/cmcfadden/AR.js/master/aframe/build/aframe-ar.js" />
    <script>
      THREEx.ArToolkitContext.baseURL = 'https://raw.githack.com/jeromeetienne/ar.js/master/three.js/'
    </script>
  </head>

  <body style="margin: 0; overflow: hidden;">
    <a-scene
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
        gps-camera
        rotation-reader
        far="900000"
      />
    </a-scene>
  </body>
</template>