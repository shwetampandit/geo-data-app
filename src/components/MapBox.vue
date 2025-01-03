<template>
  <div id="map" :style="{ width: '100%', height: '500px' }"></div>
</template>

<script>
import mapboxgl from "mapbox-gl";

export default {
  name: "MapBox",
  props: {
    accessToken: {
      type: String,
      required: true,
    },
    center: {
      type: Array,
      default: () => [73.8567, 18.5204], // Pune, India
    },
    zoom: {
      type: Number,
      default: 9,
    },
    markers: {
      type: Array,
      default: () => [], // Expecting an array of { lng, lat } objects
    },
  },
  data() {
    return {
      map: null,
    };
  },
  mounted() {
    mapboxgl.accessToken = this.accessToken;
    this.map = new mapboxgl.Map({
      container: "map",
      style: "mapbox://styles/mapbox/streets-v11",
      center: this.center,
      zoom: this.zoom,
    });

    this.map.on("load", () => {
      console.log("Map loaded successfully");
      this.addMarkers(); // Add markers once the map is loaded
    });

    this.map.on("error", (e) => {
      console.error("Map error:", e);
    });
  },
  methods: {
    addMarkers() {
      if (this.markers.length > 0) {
        this.markers.forEach(({ lng, lat }) => {
          new mapboxgl.Marker()
            .setLngLat([lng, lat])
            .addTo(this.map);
        });
      }
    },
  },
  beforeUnmount() {
    if (this.map) {
      this.map.remove();
    }
  },
};
</script>

<style scoped>
#map {
  width: 100%;
  height: 100%;
  position: relative;
}
</style>
