<template>
    <div class="col-md-9">
        <div id="map" class="map"></div>
    </div>
</template>

<script>
    import svgIcons from '../assets/icons.json'

    // voir tuto : https://travishorn.com/interactive-maps-with-vue-leaflet-5430527353c8
    export default {
        props: ["selected", "selectedColor"],
        data () {
            return {
                map       : null,
                tileLayer : null,
                markerList: [],
            }
        },
        mounted() {
            this.initMap();
        },
        methods: {
            initMap() {
                this.map = L.map('map').setView([44.4491, 1.454], 14);
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
                        for (let marker of this.markerList) {
                            this.map.removeLayer(marker)
                        }

                        let placesList = this.selected.places
                        let infosList = [];

                        for (let index in placesList) {
                            let infos = [];

                            infos.push(placesList[index].lat)
                            infos.push(placesList[index].lon)
                            infos.push(placesList[index].description)
                            infosList.push(infos)
                        }

                        for (let index in infosList) {
                            let myCustomColour = this.selectedColor
                            let longitude = infosList[index][0]
                            let latitude = infosList[index][1]
                            let customIcon =    L.icon({
                                                    iconUrl: svgIcons[this.selected.icon],
                                                    iconSize: [30, 30],
                                                })


                            let marker = L.marker(
                                                [longitude, latitude],
                                                {icon: customIcon},

                                                )
                                            .bindPopup(infosList[index][2])
                                            .addTo(this.map)
                            this.markerList.push(marker)
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
        width:  100vw;
    }   
</style>