<template>
  <v-map :zoom=10 :center="initialLocation">
    <v-tilelayer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></v-tilelayer>
    <v-rotated-marker v-for="l in locations" :key="l.id" 
      :lat-lng="l.latlng" 
      :icon="icon" 
      @click="handleMarkerClick(l)"
      :rotationAngle="l.yaw">
    </v-rotated-marker>
  </v-map>
</template>

<script>
  import { Icon, LatLng } from 'leaflet'
  import { LMap, LTileLayer, LMarker } from 'vue2-leaflet'
  import Vue2LeafletRotatedMarker from './Vue2LeafletRotatedMarker'
  import iconUrl from 'leaflet/dist/images/marker-icon.png'
  import shadowUrl from 'leaflet/dist/images/marker-shadow.png'

  function rand(n) {
    let max = n + 0.1
    let min = n - 0.1
    return Math.random() * (max - min) + min;
  }

  export default {
    components: {
      'v-map': LMap,
      'v-tilelayer': LTileLayer,
      'v-marker': LMarker,
      'v-rotated-marker': Vue2LeafletRotatedMarker
    },
    methods: {
      handleMarkerClick(l){
        l.yaw+=20;
      }
    },
    data () {
      let locations = []
      for (let i = 0; i < 10; i++) {
        locations.push({
          id: i,
          yaw:0,
          latlng: new LatLng(rand(-34.9205), rand(-57.953646)),
          text: 'Hola ' + i
        })
      }
      let icon = new Icon({iconUrl, shadowUrl})
      return {
        locations,
        icon,
        clusterOptions: {},
        rotationAngle:45,
        initialLocation: new LatLng(-34.9205, -57.953646)
      }
    },
    mounted() {
      setTimeout(() => {
        console.log('done')
        this.$nextTick(() =>{
          this.clusterOptions = { disableClusteringAtZoom: 11 }
        });
      }, 5000);
    }
  }
</script>

<style>
  @import "~leaflet/dist/leaflet.css";
  html, body {
    height: 100%;
    margin: 0;
  }
</style>