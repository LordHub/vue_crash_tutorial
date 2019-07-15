<template>

    <div>
        <div :key="todo.id" v-for="todo in todos">
            <h1>{{todo.title}}</h1>
        </div>

    </div>
</template>

<script>
    export default {
        name: "Todos",
        props: ["todos"]
    }
</script>

<style scoped>

</style>