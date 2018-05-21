# vue2-leaflet-rotatedmarker

This is a [rotatedmarker plugin](https://github.com/Leaflet/Leaflet.rotatedmarker) extension for [vue2-leaflet package](https://github.com/KoRiGaN/Vue2Leaflet)

## Install

    npm install --save vue2-leaflet-rotatedmarker

## Demo

    git clone git@github.com:jperelli/vue2-leaflet-rotatedmarker.git
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
      <v-rotated-marker>
        <v-marker v-for="c in cases" v-if="c.location !== null" :lat-lng="c.latlng">
          <v-popup :content="c.tooltipContent"></v-popup>
        </v-marker>
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

### on &lt;style&gt; add

    @import "~leaflet.rotatedmarker/dist/rotatedmarker.css";
    @import "~leaflet.rotatedmarker/dist/rotatedmarker.Default.css";

## Access rotatedmarker layer directly

If you need to access other markecluster methods, like [refreshClusters()](https://github.com/Leaflet/Leaflet.rotatedmarker#refreshing-the-clusters-icon), you can do it with a ref on the rotatedmarker vue element and using the `mapObject` property

    ...
    <v-rotated-marker ref="clusterRef">
      ...
    </v-rotated-marker>
    ...

    ...
    this.$refs.clusterRef.mapObject.refreshClusters()
    ...


## Develop and build

    npm install
    npm run build

## Author

[Julián Perelli](https://jperelli.com.ar/)

### Contributors

 - [Ahmet Özışık](https://github.com/aozisik)
 - [Nader Toukabri](https://nader.tech)

## License

MIT
