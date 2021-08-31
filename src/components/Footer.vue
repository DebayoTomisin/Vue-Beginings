<template>
    <footer>
        <p> Copyright &copy; {{ new Date().getYear()}} </p>
        <router-link to="/about">About</router-link>
    </footer>
</template>

<script>
    export default {
        
    }
</script>

<style  scoped>
footer
{
    margin-top: 30px;
    text-align: center;
}
</style>