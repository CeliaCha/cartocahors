<template>

    <div class="container-fluid" >
        <div class="row">

            <Menu/>
            <CityMap/>

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

    }

</script>


<style>

</style>
