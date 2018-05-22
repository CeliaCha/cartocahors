<template>
    <div>
        <div v-for="item in list" :key="item.name">
            <h3>{{ item.name }}</h3>
            <Subcategorie :data="item"/>
        </div>


    </div>
</template>

<script>
import Subcategorie from './Subcategorie'
import json from "../assets/places.json";

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
    // DEV
    // for (let item in this.list) {
    //   console.log(this.list[item].name);
    // }
    console.log(this.categoriesNames);
    console.log(this.subcategories);
    console.log(this.places);
  },
  computed: {
    categoriesNames() {
        let categoriesNames = []
        for (let item in this.list) {
            categoriesNames.push(this.list[item].name)
        }
        return categoriesNames
    },
    subcategories() {
      let subcategories = [];
      for (let item in this.list) {
        subcategories.push(this.list[item].children);
      }
      return subcategories;
    },
    places() {
      let places = [];
      for (let item in this.subcategories) {
        places.push(this.subcategories[item].places);
      }
      return places;
    }
  }
};
</script>

<style scoped>
</style>