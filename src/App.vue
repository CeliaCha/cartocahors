<template>
    <div class="container-fluid" >
        <div class="row">

            <Menu v-on:userChoice="passUserChoice" :list="jsonFile"/>
            <CityMap :selected="selectedPlaces" :selectedColor="selectedColor"/>

        </div>
    </div>
</template>

<script>
    import Menu from './components/Menu'
    import CityMap from './components/CityMap'
    import json from './assets/places.json'

    export default {
        name: 'App',
        components: {
            Menu,
            CityMap
        },
        data() {
            return {
                selectedPlaces: {},
                selectedColor: "",
                jsonFile: json
            }
        },
        
        methods: {
            passUserChoice(toto) {
                this.selectedPlaces = toto[0]
                this.selectedColor = toto[1]
            }
        },
    }
</script>

<style>
</style>
