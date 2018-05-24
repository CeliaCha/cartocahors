<template>
    <div class="container-fluid" >
        <div class="row">

            <Menu v-on:userChoice="passUserChoice"/>
            <CityMap :selected="selectedPlaces"/>

        </div>
    </div>
</template>


<script>
    import Menu from './components/Menu'
    import CityMap from './components/CityMap'

    export default {
        name: 'App',
        components: {
            Menu,
            CityMap
        },

        data() {
            return {
                selectedPlaces: {}
            }
        },

        methods: {
            passUserChoice(places) {
                this.selectedPlaces = places
            }
        },
    }
</script>


<style>
</style>
