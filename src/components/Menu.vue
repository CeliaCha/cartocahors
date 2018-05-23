<template>
    <div>
        <div v-for="item in list" :key="item.name" class="category">
            <b-btn v-b-toggle="item.name" class="m-1">{{ item.name }}</b-btn>
            <b-collapse :id="item.name">
                <Subcategorie v-on:userChoice="passUserChoice" :data="item"/>
            </b-collapse>
        </div>
    </div>
</template>

<script>
import Subcategorie from './Subcategorie'
import json from "../assets/places.json"

export default {
  name: "Menu",
  components : {
      Subcategorie
  },
  data() {
    return {
      list: json
    }
  },
  mounted() {

  },
  computed: {
    
  },
  methods: {
      passUserChoice(places) {
        this.$emit('userChoice', places)
      }
    },
}

</script>

<style scoped>
    b-btn {
        min-width: 300px;
    }
</style>