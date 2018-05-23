<template>

    <div class="container">
        <div class="row">
            
            <div class="col-md-12">
                <div id="map" class="map"></div>
            </div>

       </div>
    </div>

</template>


<script>
// voir tuto : https://travishorn.com/interactive-maps-with-vue-leaflet-5430527353c8
export default {
  /* Data properties will go here */
  data() {
    return {
      map: null,
      tileLayer: null,
      layers: []
    };
  },
  props: ["selected"],

  watch: {
    selected: {
      handler() {
        if (this.selected.places) {
          let placesList = this.selected.places
          console.log(placesList[0])
          let coordsList = []
          for (let index in placesList) {
            let coords = []
            coords.push(placesList[index].lat)
            coords.push(placesList[index].lon)
            coordsList.push(coords)
          }
          
          for (let index in coordsList) {
              let longitude = coordsList[index][0]
              let latitude = coordsList[index][1]
              let marker = L.marker([longitude, latitude]).addTo(this.map);
          }
          // var marker = L.marker([44.4491, 1.43663]).addTo(this.map);

        } 
      }
    }
  },

  /* Code to run when app is mounted */
  mounted() {
    this.initMap();
    this.initLayers();
    //console.log(this.selected.places);
  },

  /* Any app-specific functions go here */
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
      
    },

    initLayers() {}
  }
};
</script>


<style scoped>
.map {
  height: 90vh;
}
</style>