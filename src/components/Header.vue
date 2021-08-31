<template>
    <header>
        <h1>{{title}} </h1>
        <Button v-show='homePage' @btn-click="$emit('toggle-add-task')" :color="showAddTask ? 'red': 'green'" :text="showAddTask ? 'Close' : 'Add Task' " />
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
            },
            showAddTask: Boolean,
        },
        components: {
            Button
        },
        emit : ['toggle-add-task'],
        computed: {
            homePage(){
                if(this.$route.path === '/') {
                    return true
                } else{
                    return false
                }
            }
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