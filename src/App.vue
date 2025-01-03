<template>
  <div>
    <!-- <h1>Mapbox Example</h1> -->
    <MapBox 
      :accessToken="mapboxToken"
      :center="[73.8567, 18.5204]" 
      :zoom="12"
      :markers="[
        { lng: 73.82735, lat: 18.481 }, 
        { lng: 73.843925, lat: 18.506231 },
      ]"
    />
  </div>
</template>

<script>
import MapBox from "./components/MapBox.vue";

export default {
  name: "App",
  components: { MapBox },
  data() {
    return {
       mapboxToken:"pk.eyJ1Ijoic2h3ZXRhbXBhbmRpdCIsImEiOiJjbTVmZTQ5ZXMyZWppMnVzN2FmdG9pdW1zIn0.8s3PyySrPUQp7kvhNglbig",
    };
  },
};
</script>