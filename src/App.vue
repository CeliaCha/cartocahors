<template>
    <div id="app">
      <Menu/>
      <CityMap/>
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
