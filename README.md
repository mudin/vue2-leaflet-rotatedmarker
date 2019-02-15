# vue2-leaflet-rotatedmarker

This is a [RotatedMarker plugin](https://github.com/bbecquet/Leaflet.RotatedMarker) extension for [vue2-leaflet package](https://github.com/KoRiGaN/Vue2Leaflet)

## Install

    npm install --save vue2-leaflet-rotatedmarker

## Demo

    git clone https://github.com/imudin/vue2-leaflet-rotatedmarker
    cd vue2-leaflet-rotatedmarker
    yarn
    yarn example

    # or alternatively using npm
    npm install
    npm run example

Then you should be able to navigate with your browser and see the demo in http://localhost:4000/

You can see the demo code in the file [example.vue](example.vue)

## Usage

### on &lt;template&gt; add

something like this

    <v-map :zoom=10 :center="initialLocation">
      <v-icondefault :image-path="'/statics/leafletImages/'"></v-icondefault>
      <v-tilelayer url="http://{s}.tile.osm.org/{z}/{x}/{y}.png"></v-tilelayer>
      <v-rotated-marker v-for="l in locations" :key="l.id" 
        :lat-lng="l.latlng" 
        :icon="icon" 
        @click="handleMarkerClick(l)"
        :rotationAngle="l.rotationAngle">
    </v-rotated-marker>
    </v-map>

### on &lt;script&gt; add

#### option 1

In the same template file, at `<script>` part, this will make the component available only to the template in this file

    import Vue2LeafletRotatedMarker from 'vue2-leaflet-rotatedmarker'
    ...
    export default {
      ...
      components: {
        'v-rotated-marker': Vue2LeafletRotatedMarker
        ...
      },
      ...
    }

#### option 2

At main Vue configuration, this will make the component available to all templates in your app

    import Vue from 'vue'
    import Vue2LeafletRotatedMarker from 'vue2-leaflet-rotatedmarker'
    ...
    Vue.component('v-rotated-marker', Vue2LeafletRotatedMarker)

## Develop and build

    npm install
    npm run build

## Author

[mudin](https://github.com/mudin/)


## License

MIT
rotated marker plugin extension for vue2-leaflet package
