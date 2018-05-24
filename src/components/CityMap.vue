<template>
    <div class="col-md-9">
        <div id="map" class="map"></div>
        <img src="../assets/icons/primaire.svg" alt="bla">
    </div>
</template>



<script>

import bidouillage from '../assets/bidouillage.json'

// voir tuto : https://travishorn.com/interactive-maps-with-vue-leaflet-5430527353c8
export default {
  data() {
    return {
      map: null,
      tileLayer: null
    };
  },
  props: ["selected"],

  mounted() {
    this.initMap();
  },

  methods: {
    initMap() {
      this.map = L.map("map").setView([44.4491, 1.43663], 14);
      this.tileLayer = L.tileLayer(
        "https://cartodb-basemaps-{s}.global.ssl.fastly.net/rastertiles/voyager/{z}/{x}/{y}.png",
        {
          maxZoom: 18,
          attribution:
            '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, &copy; <a href="https://carto.com/attribution">CARTO</a>'
        }
      );

      this.tileLayer.addTo(this.map);
    }
  },

  watch: {
    selected: {
      handler() {
        if (this.selected.places) {
          let placesList = this.selected.places;
          let infosList = [];

          for (let index in placesList) {
            let infos = [];

            infos.push(placesList[index].lat)
            infos.push(placesList[index].lon)
            infos.push(placesList[index].description)
            infos.push(placesList[index].description)
            infosList.push(infos)
          }

          for (let index in infosList) {
            let longitude = infosList[index][0]
            let latitude = infosList[index][1]
            console.log(this.selected.icon);

            let customIcon = L.icon({
                //iconUrl : 'icons/verre.svg', 
                iconUrl : bidouillage[this.selected.icon],
                iconSize: [40, 40],
            })
            
            L.marker([longitude, latitude], {icon: customIcon})
              .bindPopup(infosList[index][2])
              .addTo(this.map)
          }
        }
      }
    }
  }
};
</script>


<style scoped>
.map {
  height: 100vh;
  width: 100vw;
}
</style>