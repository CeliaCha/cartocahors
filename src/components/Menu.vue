<template>
    <div class="col-md-3">
        <div v-for="item in list" :key="item.id">

            <b-btn v-b-toggle="item.id" variant="primary" class="btn-block m-1 button text-left">
                {{ item.name }}
            </b-btn>
            
            <b-collapse :id="item.id">
                <Subcategorie v-on:userChoice="passUserChoice" :data="item.children"/>
            </b-collapse>

        </div>
    </div>
</template>


<script>
    import Subcategorie from './Subcategorie'
    import json from "../assets/places.json"

    export default {
        components : {
            Subcategorie
        },
        data() {
            return {
                list: json
            }
        },
        methods: {
            passUserChoice(item) {
                this.$emit('userChoice', item)
            }
        },
    }
</script>


<style scoped>
    button {
        font-weight: bolder;
        font-family: 'Quicksand', sans-serif;
    }
    button::first-letter {
        text-transform: uppercase;
    }
</style>