<template>
  <div ref="mapContainer" class="map-container"></div>
</template>
<script>
import mapboxgl from 'mapbox-gl';
mapboxgl.accessToken = 'pk.eyJ1Ijoic2h3ZXRhbXBhbmRpdCIsImEiOiJjbTVmZTQ5ZXMyZWppMnVzN2FmdG9pdW1zIn0.8s3PyySrPUQp7kvhNglbig';
mapboxgl.config.REQUIRE_TELEMETRY = false;
export default {
  mounted() {
  const map = new mapboxgl.Map({
    container: this.$refs.mapContainer,
    style: "mapbox://styles/mapbox/streets-v12", // Replace with your preferred map style
    center: [-71.224518, 42.213995],
    zoom: 9,
  });

  this.map = map;
},
unmounted() {
  this.map.remove();
  this.map = null;
}
};
</script>
<style>
.map-container {
  flex: 1;
}
</style>