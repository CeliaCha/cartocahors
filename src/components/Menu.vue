<template>
    <div>
        <div v-for="item in list" :key="item.name" class="category">
            <b-btn v-b-toggle="item.name" class="m-1">{{ item.name }}</b-btn>
            <b-collapse v-bind:id="item.name">
                <Subcategorie :data="item"/>
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
    };
  },
  mounted() {
    console.log(this.categoriesNames)
    console.log(this.subcategories)
  },
  computed: {
    
  }
}

</script>

<style scoped>
    b-btn {
        min-width: 300px;
    }
</style>