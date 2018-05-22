<template>
    <div>
        <div v-for="item in data.children" :key="item.name" @click='selectSubCat(item)'>
            {{ item.name }}
        </div>
    </div>
</template>

<script>
    export default {
        name : 'Subcategorie',
        props : ['data'],
        methods: {
            selectSubCat(places) {
                console.log(places)
                this.$emit('categorySelected', places)
            }
        },
        
    }
</script>

<style scoped>

</style>