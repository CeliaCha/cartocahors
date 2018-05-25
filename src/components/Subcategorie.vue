<template>
    <div >
        <div v-for="item in data.children" :key="item.id" @click='passUserChoice(item, data.color)' class="sub m-2">
            {{ item.name }}
        </div>
    </div>
</template>

<script>
    export default {
        props : ['data'],
        methods: {
            passUserChoice(item, color) {
                this.$emit('userChoice', [item, color])
            }
        }, 
    }
</script>

<style scoped>
    .sub {
        color: #007BFF;
        text-transform: lowercase;
        padding-left: 5%;
        font-family: 'Quicksand', sans-serif;
    }
    .sub::first-letter {
        text-transform: uppercase;
    }
    .sub:hover {
        color:rgba(29, 74, 122, 0.733);
        cursor: pointer;
    }
</style>