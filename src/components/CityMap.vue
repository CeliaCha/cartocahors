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
        props: ["selected"],

        mounted() {
            this.initMap();
        },

        methods: {
            initMap() {
                this.map = L.map('map').setView([44.4491, 1.43663], 14);
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

        watch: {
            selected: {
                handler() {
                    if (this.selected.places) {
                        let placesList = this.selected.places
                        let coordsList = []

                        for (let index in placesList) {
                            let coords = []

                            coords.push(placesList[index].lat)
                            coords.push(placesList[index].lon)
                            coordsList.push(coords)
                        }

                        for (let index in coordsList) {
                            let longitude   =   coordsList[index][0]
                            let latitude    =   coordsList[index][1]
                            let marker      =   L.marker([longitude, latitude]).addTo(this.map);
                        }
                    }
                }
            }
        },
    };
</script>


<style scoped>
    .map {
        height: 100vh;
        width: 100vw;
    }
</style>