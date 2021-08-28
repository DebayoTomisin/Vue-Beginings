<template>
    <button :style="{background: color}" class="btn">{{text}}</button>
</template>

<script>
    export default {
        name: 'Button',
        props: {
            text: String,
            color: String
        },

        methods: {
            
        }
    }
</script>

<style lang="scss" scoped>
     

</style>