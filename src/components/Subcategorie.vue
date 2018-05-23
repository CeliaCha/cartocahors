<template>
    <div>
        <div v-for="item in data.children" :key="item.name" @click='passUserChoice(item)'>
            {{ item.name }}
        </div>
    </div>
</template>

<script>
    export default {
        name : 'Subcategorie',
        props : ['data'],
        methods: {
            passUserChoice(places) {
                this.$emit('userChoice', places)
            }
        },
        
    }
</script>

<style scoped>

</style>