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
        data () {
            return {
                map: null,
                tileLayer: null,
                layers: [],
            }
        },

        /* Code to run when app is mounted */
        mounted() {
            this.initMap();
            this.initLayers();          },

        /* Any app-specific functions go here */
        methods: {

            initMap() {
                
                this.map = L.map('map').setView([38.63, -90.23], 12);

                this.tileLayer = L.tileLayer(
                    'https://cartodb-basemaps-{s}.global.ssl.fastly.net/rastertiles/voyager/{z}/{x}/{y}.png',
                    {
                        maxZoom: 18,
                        attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, &copy; <a href="https://carto.com/attribution">CARTO</a>',
                    }
                );

                this.tileLayer.addTo(this.map);
            },

            initLayers() {},
        },
    }

</script>


<style scoped>

    .map {
        height: 90vh;
    }

</style>