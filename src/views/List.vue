<template>
    <div>
        <h1>List</h1>
        <hr>
        <table v-if="tasks.length">
        
        </table>
        <p v-else>no tasks</p>
    </div>
</template>

<script>
export default {
    computed: {
        tasks(){
            return this.$store.getters.tasks
        }
    }
}

</script>

<style>


</style>