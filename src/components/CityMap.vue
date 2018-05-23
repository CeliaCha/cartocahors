<template>

    <div class="col-md-9">
        <div id="map" class="map"></div>
    </div>

</template>


<script>

    // voir tuto : https://travishorn.com/interactive-maps-with-vue-leaflet-5430527353c8
    export default {

        data () {
            return {
                map: null,
                tileLayer: null,
            }
        },

        mounted() {
            this.initMap();
        },

        methods: {

            initMap() {

                this.map = L.map('map').setView([44.4491, 1.43663], 15);

                this.tileLayer = L.tileLayer(
                    'https://cartodb-basemaps-{s}.global.ssl.fastly.net/rastertiles/voyager/{z}/{x}/{y}.png',
                    {
                        maxZoom: 18,
                        attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>, &copy; <a href="https://carto.com/attribution">CARTO</a>',
                    }
                );

                this.tileLayer.addTo(this.map);
            },
        },
    }

</script>


<style scoped>

    .map {
        height: 100vh;
        width: 100vw;
    }

</style>