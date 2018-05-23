<template>
    <div id="app">
      <Menu v-on:userChoice="passUserChoice"/>
      <CityMap :selected="selectedPlaces"/>
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
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
