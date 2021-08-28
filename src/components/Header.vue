<template>
    <header>
        <h1>{{title}} </h1>
        <Button color="red" text="Add Task" />
    </header>
</template>

<script>
    import Button from "./Button"
    export default {
        name: 'Header',
        props: {
            title : {
                type : String, // there are several was of declaring props, in this case the name of the prop is title with type string and a default value.
                default: 'Hello There'
            }
        },
        components: {
            Button
        }
    }
</script>

<style  scoped>
    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }

</style>